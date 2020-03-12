
Before you start you'll need a local instance of postgres.

 
### The Python part:

#### Set up:
- create two databases, one called 'source' and one called 'target'
- run the queries in `set_up_python.sql` while connected to the 'source' database

#### Task
- Create an ETL process in Python that will extract the `address` and `company` tables from the source database and load them into the 'target' database
- the loading process is insert only and the ETL process should not insert a row if it already exists in the target table
- the ETL process should have some way of tracking when it last successfully ran and only extract data that was created after it last successfully ran
- write tests to show your code works as expected
- please add a requirements file for any libraries you use
