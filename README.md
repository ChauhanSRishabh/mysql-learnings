# mysql-learnings

## SQL vs MySQL

- SQL is a language used for querying a database. MySQL is a database software which uses SQL to query the database. Basically a Database on which SQL works.
- SQL runs on top of MySQL to basically query the database. MySQL use SQL to query databases and to work with it at the same time.
- SQL is used in managing RDBMS. MySQL is an RDBMS which uses SQL to perform operations such as storing, retrieval and modification of a database

## Installing MySQl(MacOS)

- To install MySQL enter this command on terminal : `$ brew install mysql`  
If brew is not installed, before running the above command, run this command on Terminal - `$ /bin/bash -c "$(curl -fsSL https:#raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

- You'll also need to install MySQLWorkbench, click [here](https:#dev.mysql.com/downloads/workbench/) to install.

### Additional configuration

#### **Homebrew**

- Install **brew services** first : `$ brew tap homebrew/services`
- Load and start the MySQL service : `$ brew services start mysql`  
Expected output : **Successfully started `mysql` (label: homebrew.mxcl.mysql)**
    
    The `brew services start mysql` instruction is equivalent to :
    
    ```
    $ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
    $ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
    
    ```
    
- Check if the MySQL service has been loaded : `$ brew services list`
- Verify the installed MySQL instance : `$ mysql -V`.  
- To stop the MySQL service : `$ brew services stop mysql`

## Rules in MySQL

- Keywords aren't case-sensitive. Can be written in all-caps, all lower case, or combination of upper and lower case. Although it is **best practice to write them in uppercase**.   
- If you want to write 2 different SQL queries in a single file, you need semicolon(**;**) to separate them.
- To write a string in SQL, write it inside single-quotes(**‘‘**) quotes to distinguish it from keywords. eg - ‘string’

## Database for a Music Record Company

### Working with MySQLWorkbench
**How to execute queries and notice if changes made took effect**
```
# ⚡️(executes everything inside the file or what is highlighted) 
# ⚡️ with a cursor inside(execute statement where the cursor is)

# UI does not refresh on it's own
# Go to Schemas section on the left
# Refresh it
# you'll see record_company database
```

### Creating and Dropping a database
#### CREATE
```
CREATE DATABASE record_company;
```
#### DROP
```
DROP DATABASE record_company; # something you'll never use as dropping removes all of the data that is inside the database
```

### Tell SQL where to run our SQL queries, on which database
```
USE record_company;

# Execute it with ⚡️ and you'll notice it gets bolded
# Now every SQL query that we write will be executed on this database
```

### Create, Alter and Drop a Table
#### CREATE
```
CREATE TABLE test(
test_column INT
);

# All the above 3 lines are a single command
# execute it, refresh, notice there's a table named test inside Tables, inside record_company database
```
#### ALTER
Used to change properties of a table after we've created it.  
Let's add another column to a table named 'test' that we created.
```
ALTER TABLE test
ADD another_column VARCHAR (255); # VARCHAR is way of telling SQL that the type is String
# we could have written the above 2 lines as a single line but SQL doesn't care about line breaks in the statement, it just reads it until it sees the ;
```
#### DROP
```
DROP TABLE test;
```

## CRUD Operations

### Working on our record company database

### CREATE
#### Primary Key/ID/Auto Increment/Not NULL
```
CREATE DATABASE record_company;
USE record_company;

CREATE TABLE bands (
id INT NOT NULL AUTO_INCREMENT,
name VARCHAR(255) NOT NULL,
PRIMARY KEY (id)
);
```
- 'id' : What if a band has the same name as another? Use to uniquely a identify a row from other rows
- AUTO_INCREMENT : We want id to be automatically generated whenever we add a band
- NOT NULL : to make sure our band always have a name, we specify this keyword
- PRIMARY KEY (id) : id is going to be the identifier of out table, i.e., the primary identifying column of our table

**MySQLWorkbench**
```
# Execute the above written query and then Refresh the schemas section.
# Notice there's a table named bands inside Tables 
# and inside bands we have 2 columns for id and name
# We also have a subsection named Indexes for our PRIMARY KEY which tells SQl that this is what distinguishes our band from the other band records in the table 
```