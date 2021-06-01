# DisasterManagementApplication
This application helps in collecting and sharing disaster information collected by users in real time and ensuring the safety of victims. Furthermore, Disaster Management rescuers can monitor the position and can search for victims faster.
# Architecture of the Application
![image](https://user-images.githubusercontent.com/84661500/120296489-765d3600-c2c8-11eb-9cec-12857ca846c9.png)

The web application architecture describes the relationships between the applications, the database and the middleware systems. The front-end, often referred to as the client-side, responds to user input and interacts within the browser. The main goal of the client is to collect data from users. The front-end part is written in HTML, CSS and JavaScript languages. The back-end of an app is often referred to as the server-side. A server can run any application that can respond to HTTP requests. The server-side is in charge of generating the requested page as well as storing various types of data (text, images, files, etc.), such as user profiles and user feedback. The end-user is never aware of it. Back-end is done in Java.
# Application Design
  1. Sequence flow of Rescuer/Admin Login
  
![image](https://user-images.githubusercontent.com/84661500/120296974-f2577e00-c2c8-11eb-9806-37de86381c8a.png)

The sequence flow of Rescuer/Admin login is represented in above figure. The client-side of the application shows a login page for rescuers/admins and a helpline page for victims. When a rescuer/admin tries to login with the required credentials a request will be sent to the application from the browser. The application forwards the request to the rescuer API to validate the credentials given by the rescuer. Next, the rescuer API approaches the database with a request to authenticate the credentials. Then the database server examines these credentials and if it matches to the one which are in the server it responds with an OK response to the API. The API then generates a token to start the session for the rescuer/admin and this session will be active for few minutes.
