Test Cases for ETL Process:

Assuming DB connection is successful, I have tested for following cases:


Case 1: 1st Time ETL Run

		Expected Outcome: 
							a. All the records from the `address` and `company` tables of the Source DB should be moved to Target DB
							b. Log the date, status and row counts into the error logging table and log file.

		
Case 2: Run ETL process `without` any new records created in Source after last successful ETL run

		Expected Outcome: 
							a. No records from the `address` and `company` tables of the Source DB should be moved to Target DB
							b. Log the date, status and row counts as 0 (ZERO) into the error logging table and log file.
							

Case 3: Run ETL process 'with' a new records created in Source after last successful ETL run

		--Inserted one new record into company table
		INSERT INTO public.company (company_id,status,rating_threshold,company_name,foundation_date,legal_form,created_at)
		VALUES ('bbb','kkk','FALSE','kkk','1981-04-03','kkk','2020-02-26')

		--Inserted one new record into address table
		INSERT INTO public.address (id,company_id,country,postal_code,city,district,street,street_number,addition,created_at)
		VALUES (9999999,'bbb','DE','55767','bbb','','','','','2020-02-26')
		
		Expected Outcome: 
							a. All new records from the `address` and `company` tables of the Source DB should be moved to Target DB. The new company   with company_id = `bbb` and new address with id = 9999999 will be inserted to the target database.
							b. Log the date, status and row counts (1) into the error logging table and log file.
							

Note:

	1. All the logging is done into table -> `etl_process_log` in Target DB
	2. Additonal logs can be found in log file - `2020-02-24_ETL_log.txt` which will be created on date basis and all executions will be appened to   it for a day with timestamp.