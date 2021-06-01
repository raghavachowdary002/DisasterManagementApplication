# DisasterManagementApplication
This application helps in collecting and sharing disaster information collected by users in real time and ensuring the safety of victims. Furthermore, Disaster Management rescuers can monitor the position and can search for victims faster.
# Architecture of the Application
![image](https://user-images.githubusercontent.com/84661500/120296489-765d3600-c2c8-11eb-9cec-12857ca846c9.png)

The web application architecture describes the relationships between the applications, the database and the middleware systems. The front-end, often referred to as the client-side, responds to user input and interacts within the browser. The main goal of the client is to collect data from users. The front-end part is written in HTML, CSS and JavaScript languages. The back-end of an app is often referred to as the server-side. A server can run any application that can respond to HTTP requests. The server-side is in charge of generating the requested page as well as storing various types of data (text, images, files, etc.), such as user profiles and user feedback. The end-user is never aware of it. Back-end is done in Java.
# Application Design
1. Sequence flow of Rescuer/Admin Login
  
![image](https://user-images.githubusercontent.com/84661500/120296974-f2577e00-c2c8-11eb-9806-37de86381c8a.png)

The sequence flow of Rescuer/Admin login is represented in above figure. The client-side of the application shows a login page for rescuers/admins and a helpline page for victims. When a rescuer/admin tries to login with the required credentials a request will be sent to the application from the browser. The application forwards the request to the rescuer API to validate the credentials given by the rescuer. Next, the rescuer API approaches the database with a request to authenticate the credentials. Then the database server examines these credentials and if it matches to the one which are in the server it responds with an OK response to the API. The API then generates a token to start the session for the rescuer/admin and this session will be active for few minutes.

2. Flow Diagram for Ticket Generation

![image](https://user-images.githubusercontent.com/84661500/120297498-701b8980-c2c9-11eb-99f1-a0bde753ecd8.png)

In this page we setup a helpline page where a victim in need can reach out for help by filling in the details. The details in which the victim can fill are the name, age, current location, number of other victims around and the details of emergency contact. After filling all these details, the browser sends the details to the API as a request to create a ticket. The API processes this request and after storing the details in the database a ticket will be created. The API logs the ticket ID in the allocation service and sends the response to the browser as success.

3. Ticket Allocation Service

![image](https://user-images.githubusercontent.com/84661500/120297609-8d505800-c2c9-11eb-9a71-1558eeb2c8f4.png)

The status of the tickets is defined as open, In-Progress, close and re-open. As soon as the ticket is created, the status is automatically assigned as open. If the status of the ticket is open for 15 minutes, then a rescuer will be automatically assigned to it and the status will be assigned as In-Progress. If a rescuer finishes their task by identifying the victim, he/she can close the ticket manually. By any chance is the same ticket is re-opened it will be automatically assigned to the rescuer who previously closed the ticket. 

# Installation Guide

Below are the following steps to test the application. 
1.	Clone the repository from GitHub.
2.	Download and Install IntelliJ IDEA from the below link
      https://www.jetbrains.com/idea/
3.  Now open the folder rescuer-api-main in IntelliJ IDEA. Automatically all the required packages will be downloaded and installed in the IDE. Also download Java version 11         from the plugins.
4.  Open the command prompt and change the directory to MobileComputing-Project/rescuer-api-main and execute the following commands consecutively.
      i) sudo docker build -t rescuer-app-service .
      ii) docker run -e “SPRING_APPLICATION_NAME=rescuer-app-service” -e ”server.port=8080” -p 8080:8080 --init --rm -d --name rescuer-service rescuer-app-service
5.  Open a new cmd terminal and change the directory to MobileComputing-Project/rescuer-app-ui-main and run the following commands.
      i) sudo docker build -t rescue-app-nginx .
      ii) sudo docker run --init --rm -d -p 80:80 rescue-app-nginx
6.  Open a browser and search for localhost in the URL bar. Now the application is ready and can test it by creating a ticket by entering the required details. 
7.  To check the tables in database, download the database navigator plugin from the following link and install to IDE.
      https://plugins.jetbrains.com/plugin/1800-database-navigator
8.  Go to https://id.heroku.com/login and enter the below credentials 
      Email Address: r.dhawan27@hotmail.co.u
      Password: RescuerApp@123  
9.  After logging in, click on the rescuer-app-project then go to the resources tab and click on Heroku Postgres add-ons. Now go to the Settings tab and click on view               credentials.
10. On the left panel of IntelliJ IDEA, open the DB Browser tab and open a new PostgreSQL connection. Now enter the values of Host, Database, User, Password from the Heroku         website.
    Note: These details frequently change as it is a free account. If the application come across any error, make sure to update the values from the Heroku website in PostgreSQL           connection.
11. After entering the details click apply and now the connection to the database has been established.
12. To see the tables, Expand the schemas and then expand the public and now the Tables are visible.
