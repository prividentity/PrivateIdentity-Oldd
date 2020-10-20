*describe db.sh functions*
The github repository can be found at:
git@github.com:openinfer/pollard.git

The SQL's each have a unique task at setting up the repository and then the datatable and the database. The current db.sh bash script executes the required SQL's to setup the user and the datatable and moves the access from root to the user. 
The first task performed is the allow_root.sql which moves unlocks the root access to allow a user to be created. 
The next two tasks are the datatable initiator and the user identifier, create.sql drops any existing tables and creates a new one, and create_user.sql drops any duplicate users in order to create a new unique user and it also identifies privileges so it is moved off of root. 
The bash then executes create_tables and create_indexes, which create a table with specified columns and rows, and the indexes required to navigate the table without having to navigate the table one row/column at a time. 
Once the db.sh is complete, the user can then create a generic table with load.sql, or utilize a custom bash script to generate a table which can an example can be found with table_creator.sh, the type of script doesn't matter, as long as it can insert into the already generated table. 

bash commands
db.sh
table_creator.sh
src commands
allow_root.sql
create.sql
create_user.sql
load.sql
create_indexes.sql
create_tables.sql
drop_indexes.sql