# DisasterManagementApplication
This application helps in collecting and sharing disaster information collected by users in real time and ensuring the safety of victims. Furthermore, Disaster Management rescuers can monitor the position and can search for victims faster.
# Architecture of the Application
![image](https://user-images.githubusercontent.com/84661500/120296489-765d3600-c2c8-11eb-9cec-12857ca846c9.png)

The web application architecture describes the relationships between the applications, the database and the middleware systems. The front-end, often referred to as the client-side, responds to user input and interacts within the browser. The main goal of the client is to collect data from users. The front-end part is written in HTML, CSS and JavaScript languages. The back-end of an app is often referred to as the server-side. A server can run any application that can respond to HTTP requests. The server-side is in charge of generating the requested page as well as storing various types of data (text, images, files, etc.), such as user profiles and user feedback. The end-user is never aware of it. Back-end is done in Java.
# Application Design
1. Sequence flow of Rescuer/Admin Login
  
![image](https://user-images.githubusercontent.com/84661500/120296974-f2577e00-c2c8-11eb-9806-37de86381c8a.png)

The sequence flow of Rescuer/Admin login is represented in above figure. The client-side of the application shows a login page for rescuers/admins and a helpline page for victims. When a rescuer/admin tries to login with the required credentials a request will be sent to the application from the browser. The application forwards the request to the rescuer API to validate the credentials given by the rescuer. Next, the rescuer API approaches the database with a request to authenticate the credentials. Then the database server examines these credentials and if it matches to the one which are in the server it responds with an OK response to the API. The API then generates a token to start the session for the rescuer/admin and this session will be active for few minutes.

2.Flow Diagram for Ticket Generation

![image](https://user-images.githubusercontent.com/84661500/120297498-701b8980-c2c9-11eb-99f1-a0bde753ecd8.png)

In this page we setup a helpline page where a victim in need can reach out for help by filling in the details. The details in which the victim can fill are the name, age, current location, number of other victims around and the details of emergency contact. After filling all these details, the browser sends the details to the API as a request to create a ticket. The API processes this request and after storing the details in the database a ticket will be created. The API logs the ticket ID in the allocation service and sends the response to the browser as success.

3. Ticket Allocation Service

![image](https://user-images.githubusercontent.com/84661500/120297609-8d505800-c2c9-11eb-9a71-1558eeb2c8f4.png)

The status of the tickets is defined as open, In-Progress, close and re-open. As soon as the ticket is created, the status is automatically assigned as open. If the status of the ticket is open for 15 minutes, then a rescuer will be automatically assigned to it and the status will be assigned as In-Progress. If a rescuer finishes their task by identifying the victim, he/she can close the ticket manually. By any chance is the same ticket is re-opened it will be automatically assigned to the rescuer who previously closed the ticket. 
