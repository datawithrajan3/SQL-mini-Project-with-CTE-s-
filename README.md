# SQL-mini-Project-with-Function, CET & Views-s-

---=================================---
     ---Clean up null Values---
---=================================---

---Query to check NULL values in salary column---

select 1 from job_postings_fact jpf where jpf.salary_year_avg is null and jpf.job_location = 'Germany'

---======================================---
---function for cleap up and extract data---
---======================================---

create or replace function count_jobs_company_Clean_null (p_loc varchar default 'Germany')
returns table (company_name varchar,
		       count_company int,
		       loca 		  varchar)
language plpgsql
as $$


Begin
		UPDATE job_postings_fact
   	    SET salary_year_avg = 0
        WHERE salary_year_avg IS NULL
        AND job_location = p_loc;

	    return query
		select cd.name::varchar,
		count(jpf.company_id)::INT,
		jpf.job_location::Varchar
		from job_postings_fact jpf 
	    join company_dim cd 
			on cd.company_id = jpf.company_id 
		where jpf.job_location = p_loc
		group by cd.name,jpf.job_location 
		order by count(jpf.company_id) DESC;

End;
$$; 

select count_jobs_company_Clean_null()
