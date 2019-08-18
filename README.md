# Steps to run the application:
* MySql Setup:
	* Login in my sql using username and password.
	* Create a database by typing:
		> create database todo;

* To run Backened Code:
	* Change the username and password in application.properties with your mysql username & password. 
	* Go inside the java code folder **todo-app/todo** and type:
		> mvn spring-boot:run
	* This will run the backend server and create a tables called 'todos' and 'subtasks' for us.

* In MySQL IDE run below code to insert values in the tables:
	> use todo;

	* To insert into todos table:
		> insert into todos values(1, 'Java');
		> insert into todos values(2, 'Angular');

	* To insert into subtasks table:
		> insert into subtasks values(1, 'Inheritance', 1);
		> insert into subtasks values(2, 'Class', 1);
		> insert into subtasks values(3, 'Components', 2);

* To run frontend code:
	* Go inside **todo-app/frontend** and type:
		> npm run start

* Go to http://localhost:4200 and start using the application.

# ToDo Application
A todo app:
* Front-End: Angular
* Back-End: Java, Spring
* Database: MySql


# Backend Using Spring 
* Save the deatils of database login, password and create a db called todo in applicaation.properties before running 

* To run the backend code on localhost:8080 : 
	> **mvn spring-boot:run**

* DB name: **todo**
	* url: **localhost:3306/todo** (MySql)
	* application.properties file contains db connecton details

* table name: **todos**
	- id: long (autogenerated)
	- description:string (about the todo) 

* table name: **subtasks**
	- id: long (sutogenerated)
	- description: string (sbout subtask)
	- todoId: long (id of todo to which it belongs)

* url: localhost:8080/api/todos
	* /, POST: create a todo Item
	
	> {"description": "Data Structures"}

	* /, GET: find all todo
	
	* /{id}, DELETE: delete a todo given a id in url 
	
	* /{id}, PUT: update a todo given a id in url
	> {"description": "DS"}
	
	* /{id}, GET: get subtask for that todo
	
	* /subtask, POST: create a subtask for a todo
	> { "description": "Arrays", "todoId":1 }


* Used Postman to verify all the API's calls.

## Backend Flow
When we hit a url in the postman, it goes to the controller class to map the url using RequestMapping and see the type of request and then calls the service implementation class which uses JPA to do the CRUD operations and provide us the details.

# Frontend Using Angular
* To run the angular project
> npm run start
*  Command to create new angular project (boilerplate) with project name frontend:
> ng new frontend 
* To create a component
> ng g c
* To create a service 
> ng g s
* For linking the spring server with angular server 
	* added a proxy file in root of the folder, which connect to the spring server for making the api calls from the 	   front end.
	* In package.json add this:
		> "start": "ng serve --proxy-config proxy.config.json"
* To use bootstrap and jquery add that in angular.json, remember don't add **../**
