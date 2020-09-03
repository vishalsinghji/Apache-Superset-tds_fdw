# Apache-Superset-tds_fdw
Apache-superset installation in windows  &amp; using Foreign Data wrapper to connect to Ms SQL Server.

Apache Superset Installation 

Please follow the  commands mentioned below to install apache superset.

Ubuntu(Windows by Enabling Linux Subsystem For Windows)

Step 1: Download and install Ubuntu from windows Store.



Step 2: Goto  Turn Windows Features on or off (just by searching)



3. Select  the Windows Subsystem for Linux and then press ok



Note :- After that make sure you have turned on Developer mode for windows some time you might face some issue .



After that open the ubuntu which you have installed.And enter the username & password 



After that enter the commands in ubuntu :-

1.  sudo apt update
2.  sudo apt install python3-pip
3.   pip3 --version




4.   pip3 install virtualenv
5.   sudo apt-get install python3-venv
6    python3 -m venv supersetdata


7.   . supersetdata/bin/activate


After that enter these commands 

8.    pip install --upgrade setuptools pip
9.    pip install apache-superset
10.   superset db upgrade
11.   export FLASK_APP=superset

12.   superset fab create-admin
(  Username [admin]: admin
User first name [admin]: admin
User last name [user]: admin
Email [admin@fab.org]: xyz@gmail.com
Password:
Repeat for confirmation:    )

13.   superset load_examples
14.   superset init


15.   superset run -p 8088 --with-threads --reload --debugger



Enter the url in your Browser :- http://127.0.0.1:8088/



After Sign in you will see Dashboards Explore the DashBoards











How to  Get MSSQL Data in  PostgreSql ?
      Using (Foreign Data Wrapper) tds_fdw

PostgreSql Installation
 Here I  am using PostgreSQL 12 .(PostgreSql Download Link)

tds_fdw  installation and configuration
You need to download suitable Binaries according to your Software.

For Binaries You can refer the below link .(Binary file link)
 (https://github.com/tds-fdw/tds_fdw/issues/53#issuecomment-626329771)

After downloading the binaries extract the Binary file .


After that go to PostgreSql Folder in Program files and Paste the Binary file according to given instruction.




Before creating extension check on which port your Ms sql server is Running.

Open SQL sever 2019(your version) configuration Manager.



 Open the Sql Server 2019 configuration Manager

 
Check  TCP/IP is enabled.
 3  Click on the TCP/IP and  check on which port it is running 
See if  there is port number mentioned  or not  & click ok . 


After that restart the server.

Click on the Sql server (which is running) and Restart it .




MSSQL Table Creation and accessing in Postgres  
Open Microsoft SQL Server Management Studio 18


 Open it  and we are going to create new user  first.
 Go to login and click on it to create new user.


After that write the UserName & Password and give certain permission of sysadmin(to fetch all the database if you wish)
 



Press  Ok and you will see a new user has been created.



After that we are going to log in with the new user .



As the new user it will ask for new password you can enter same password as you wish.


Press Ok you will find that you have signed into MS SQL with same UserName.


So create one Database and Table .
 
Database Name - Test
Table  Name- employee (with 4 attributes)
Schema - dbo
  
 




After that we will go to PostgreSql we will create extension and try to fetch data using Foreign Data wrapper.

1 Create Database


Enter the DataBase Name and press Save.
 

After that you will find DatabaseName in Databases.



Open Query tool


We are going to create extension(tds_fdw)
I have followed this link for syntax reference(Syntax  Link)

Step :1


After execution you can find extension.



Step 2: Foreign server Creation




You will find foreign server you created on foreign servers.
 

Step 3: We are going to create userMapping


You can see user Mappings in user Mapping that you have created.











Step 4: We will create Foreign Table

You can see created Foreign Table










Step 5:  Now we are going to Run a Query to check we can fetch Data .







