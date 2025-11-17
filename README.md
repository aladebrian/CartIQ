# SWE-Project

## Set up Virtual environment:
```bash
python -m venv env
env/Scripts/activate.bat
```

## Install dependencies:
```bash
pip install -r .\requirements.txt
```

## Create a new database table
Go to backend/api/models.py  
Type your model according to the documentation [here](https://docs.djangoproject.com/en/5.2/topics/db/models/#intermediary-manytomany)  
Create the migration files and migrate the changes:
```bash
python manage.py makemigrations
python manage.py migrate
```
## Testing and troubleshooting
make sure MySQL Command Line Client and Workbench is installed

all the variables in the above statements should be defined in your backend/.env file like so:
```bash
DB_HOST=""
DB_PORT=""
DB_USER=""
DB_NAME=""
DB_PWD=""
```
according to your specifications. DB_USER refers to the username, while DB_NAME refers to the database name. 
mine is:
```bash
DB_HOST="127.0.0.1"
DB_PORT="3306"
DB_USER="*****" 
DB_NAME="*****"
DB_PWD="*****"
```
In MySQL workbench:
create a new instance (if necessary), by clicking the + next to MySQL connections.
Connection name can be anything, but match Hostname, Port, Username, and Password  to .env file.
click OK.

start the MySQL server:
```bash
mysqld start
```
troubleshooting:
if mysqld command doesn't exist: add MySQL bin to system environment variables PATH (mine is "C:\Program Files\MySQL\MySQL Server 8.0\bin")
if mysqld command gives testing error: 
```bash
cd "<your MySQL bin path>"
mysqld --initialize
```
run the MySQL server:
```bash
cd backend
python manage.py makemigrations
python manage.py migrate
```
troubleshooting:
if makemigrations give user access denied error: create the database and set user as admin

creating the database and setting user as admin (in MySQL cli):
```bash
create database <database_name>; 
create user <user_name>@<database_host> identified by '<password>';
grant all <database_name>.* to <user_name>@<database_host>;
flush privileges;
```

run the frontend:
```bash
cd frontend
npm install
```
test the connection by creating a new user in the app, and checking the database in MySQL workbench for updates.
