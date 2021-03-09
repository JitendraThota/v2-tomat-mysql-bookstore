Objective: 
This application runs on the tomcat and connect to the mysql database.

First setup : mysql and create the database and create the tables

Queries are in the sql/Bookstore.sql file

you have source code : build with maven , you will get war

Tomcat : Take the war and deploy  to the webapps


How source code connect to the database , its in the web.xml 
WebContent/WEB-INF/web.xml

jdbc url has localhost , in future you can replace where is your db ip/endpoint.

<context-param>
		<param-name>jdbcURL</param-name>
		<param-value>jdbc:mysql://localhost:3306/bookstore</param-value>
	</context-param>

<context-param>
		<param-name>jdbcUsername</param-name>
		<param-value>root</param-value>
</context-param>

<context-param>
		<param-name>jdbcPassword</param-name>
		<param-value>GVT0SvT</param-value>
</context-param>









Local setup
===============
We have the source code in the java language.

We need to compile and build the package.

From java you can make diff packages like jar/war/ear..etc.

Here for our example we are making the war file and we will deploy 

into the tomcat webapps directory and you can access locally,

http://localhost:8080/<name>

ex: http://localhost:8080/bookstore

above context root : /bookstore , same name has to match with the 

webapps deployed file name.

This application connects to the database and stores the data of books.

CURD operations

sql/Bookstore.sql

Installations
==================

Install the java

Install the maven

    clone this project local :

Install the mysql

    setup the username and password for the mysql.

    Login to the database with root user.

    check databases: show database;

    switch to any database: use <dbname>;

    Restore the sql/Bookstore.sql to the database.

    Check the import database/export mysql database.

Goto the folder , where you have cloned , and run the below commands.

when you are running the command, you need to have pom.xml in the

same folder.

Build the prject:  mvn clean package

Get the pacakge from target and copy to the tomcat/webapps folder.


Install the tomcat

start the tomcat access the url local

access the url 

http://localhost:8080/bookstore





VM deployment
================
Application connects to the mysql/rds data

Clone this project locally.

Install the java ( Oracle/OpenJDK)-Install the JDK(not JRE)

Install the maven and setup to the path 

Validate the code as a developer

check the pom.xml

src/net/codejava/javaee/BookDAO.java

src/net/codejava/javaee/ControllerServlet.java

Goto the init method check the jdbcURL,jdbcusername,jdbc password.

We are passing those credentials in the web.xml.






Container Deployment
======================
Start/build the mysql container/image.

Setup the username and password during the image build time(customize your own password,dont use default password )

Intialize the database during the container build/image build time.


Create the container/create the database/delete the container.

Again start the container/check the database.

Use the volume concept

Create the container/create the database/delete the container.

Again start the container/check the database.






Update the database host/username/password in the web.xml

Create the tomcat docker image and copy this war file






Learning:

java:

Installation of java

Upgradation of java

Multiple java

Checking java version

Diff b/w jdk/jre (heapdump/threaddump )

mysql
Installation of mysql

Check mysql logs

Check process list

Check queries running

Install as a service    

Deadlock

Troubleshoot DB issue/Slow query/cpu/memory/network

Devops with DB : flyway db/schema injection

tomcat
installation
pre-req
heap/thread dump
slow
kill
stop/start
logs check
upgradation
install as a service


Nginx and Tomcat integration(proxy)
--------------------------------------
reverse proxy


location /bookstore {
        proxy_set_header X-Forwarded-Host $host;
        proxy_set_header X-Forwarded-Server $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://127.0.0.1:8080/bookstore/;
}

