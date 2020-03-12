I have used following libraries and DB objects to complete this taks:

Libraries:
			1. psycopg2
			2. sqlalchemy
			3. datetime
			4. pandas
			

			
DB Objects:

			1. Created one log table for logging the errors and etl status
			
				CREATE TABLE etl_process_log
							(
								id integer,
								etl_run_date date,
								etl_status text,
								etl_error_code text,
								etl_table_name text,
								etl_row_count integer
							);
						
			2. Created one SEQUENCE for auto generating ID numbers
			
				CREATE SEQUENCE error_id
								INCREMENT 1
								START 1
								MINVALUE 1
								NO MAXVALUE
								CACHE 1;

			