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

### Creating and Dropping a database
```
# Create Database command
CREATE DATABASE record_company;

# Drop Database command:
DROP DATABASE record_company;
# something you'll never use as dropping removes all of the data that is inside the database
```

### Working with MySQLWorkbench
```
# ⚡️(executes everything inside the file or what is highlighted) 
# ⚡️ with a cursor inside(execute statement where the cursor is)

# UI does not refresh on it's own
# Go to Schemas section on the left
# Refresh it
# you'll see record_company database
```

