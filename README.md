# SQL-mini-Project-with-Function, CET & Views-s-

---=================================---
     ---Clean up null Values---
---=================================---

---Query to check NULL values in salary column---

select 1 from job_postings_fact jpf where jpf.salary_year_avg is null and jpf.job_location = 'Germany'

---======================================---
---function for cleap up and extract data---
---======================================---

