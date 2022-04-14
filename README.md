# This repository has a RESTFul API for Dealer and Listing entities

This project implements the use of a RESTFull API for Dealer and his/her Listing, inclusing supports the Controller Class for a complete and customized CRUD operations

## ⚙️ Main Technologies
* 1 - **String** Boot, Security and Data
* 2 - **Swagger** API Documentation
* 3 - **Dozer** Class converter
* 4 - **HATEAOS** Supports development of a RESTFul API 
* 5 - **Jackson** Allows requeste and response in xml, yaml, json format
* 6 - **JUnit** Test Class
* 7 - **Mockito** Offers a library with different methods for performing and validating tests
* 8 - **REST Assured** Testing and validating REST services

## ⚙️ Architecture
This project was developed using the best practices in API RESTFUll development. The layers that make up the solution are listed and described below
* 1 - **Controller** In addition to implementing the endpoints for the services provided by the entity, this layer is responsible for converting the requests made in XML, JSON and YAML format to the format accepted by the backend and also converting responses to the format desired by the API user. 
* 2 - **ServiceVO** Responsible for converting VO class objects to entity classes recognized by the business layer. The VO layer implementation allows modifying the attributes of the inner classes for the user consuming the API. This new mapping increases the security of the application by hiding the real attributes of the business classes.
* 3 - **ServiceBO** In this layer are applied as business rules before the operations with the database, using a own repository data access class and other BO service classes. 

## ⚙️ UML Diagrams (Simplified)
* 1 - **Class Diagram**

![image](https://user-images.githubusercontent.com/63114961/163382563-3935977b-05bf-430b-a3ab-93b65e12166b.png)

* 2 - **Sequence Diagram**

 ![image](https://user-images.githubusercontent.com/63114961/163385585-6979664b-fffd-4f64-87a0-c976496f4161.png)
 
 * 3 - **Class Test Diagram**
 

## 📋 Business
* 1 - **Requirements**
  * 1.1 - **Listing** - A vehicle advertisement. Listing can be in one of two possible states: **published** or **draft** (available or not online)</br>
           * 1.1.1 - **Atributes** id: uuid, dealerId: uuid, vehicle: string, price: number, createdAt: date, state: draft/published 
  * 1.2 - **Car Dealer** - An owner of the advertisement
           * 1.2.1 - **Atributes** id: uuid, name: String
           * 1.2.2 - **Tier Limit** A number of published listings a dealer can have online 
  * 1.3 - **Logs**
  * 1.4 - **Exception handling**
  * 1.5 - **Documentation**
  * 1.6 - **Tests**

* 2 - **Functionality**
  * 2.1 - **Listing:** Create, Update, Get all listings of a dealer with a given state, Publish a listing
  * 2.1 - **Car Dealer:**  

* 3 - **Rules**
  * 2.1 - **Car Dealer** - An owner of the advertisement


## 🛠️ Tools Technical Requirements

* 1 - MySQL Database (SGBD Tool)
* 2 - Java 11
* 3 - IDE Development. The project was developed Eclipse Version: 2020-06 (4.16.0) Build id: 20200615-1200
* 4 - The source code from https://github.com/edfcbz/task-api-rest-spring-360agency-test
* 5 - Database client as MySql Workbench. The project choose HeidiSQL 64 bits Version 11.0.0.5919 Build 2020-03-17 17:05:04
* 6 - Http request tool as Postman  


## 🚀 Starting Database and Environment
Fellow the below step for run the project

## 🔧 Development Environment Setup - DATABASE

* 1 - Install and Run the MySQL Server (Default port)
* 3 - Install and Run the HeidiSQL
  * 3.1 - In HeidiSQL run CreateDataBaseAndData.sql file (This step will create the SCHEMA and will insert basic data into tables). For it select: File -> Load SQL file -> Press SQL Execute (Blue Icon)
  * 3.2 - After prior step refresh environmet F5 key or press icon green (Refresh)
  * 3.3 - Verify if squema was created and tables has data 

## 🔧 Development Environment Setup - DEVELOPMENT

* 1 - Run Eclipse and Import the project as "Existing Maven Project" option
* 2 - In Eclipse menu select Project -> Clean
* 3 - Open package br.com.edfcbz and locate Statup.java file. Run it as Java Application. The TomCat server will run at 8080 port
  * 3.1 - Tips: If the Eclipse console show the message "Caused by: java.net.BindException: Address already in use: bind", finalize the service in 8080 port as showed
  * 3.2 - Run CMD as Administrator and type de command line: C:\>netstat -a -n -o | findstr :8080 (This command will show a line as:
          *TCP 0.0.0.0:8080 0.0.0.0:0 LISTENING 8457 (In this example 8457 is the PID process)
  * 3.3 - Run CMD command line as Administrator: C:\>taskKill.exe /F /PID 8457 ( This command will show a line as: 
          *SUCCESS: The process with PID 8457 was terminated. ( Or similar message )
  * 3.4 - Execute 3.1 step again

## ⚙️ Testing environment
* 1 - Requesting a token (Security Layer)
  * 1.0 - Run Postman
  * 1.1 - Select a POST request and type http://localhost:8080/auth/signin
  * 1.2 - In Body section type: {
                          "username":"leandro",
                          "password":"admin123"
                        }
  * 1.3 - Select SEND button (You will receive a message with a token as below)
  ![image](https://user-images.githubusercontent.com/63114961/163141178-e52010dc-74a7-44c4-9e02-ce4680aafaf5.png)

  * 1.4 - Copy the token returned without ""

* 2 - Requesting a TomCat service
  * 1.0 - Select a GET request and type http://localhost:8080
  * 1.1 - In Header section create a new Authorization key with value: Bearer <paste here token received in step 1.3>. Tip: There is just one empty space between Bearer and token
  * 1.2 - Select SEND button. You will receive all a list with services available, as showed in image below. So, your enviroment is running...

![image](https://user-images.githubusercontent.com/63114961/163140854-fb7691cd-cd45-412b-8c78-c5fd09df6046.png)


## ⚙️ API RESTFul - Endpoints list and general informations
* 1 - **Dealer** endpoints
  * 1.0 - GET request for http://localhost:8080/dealer ( Show all Dealer registered in the Database )
  * 1.1 - GET request for http://localhost:8080/dealer/{dealerId} ( Show the Dealer details according **dealerId** informed and all Listing related )
  * 1.3 - GET request for http://localhost:8080/dealer/{dealerId}/{listingState} ( Show the Dealer by dealerId and Listing registered by listingState )
  * 1.4 - GET request for http://localhost:8080/dealer/name/{dealerName} ( Lists all dealers whose names match with the parameter, fully or not ) 
  * 1.5 - DELETE request for http://localhost:8080/dealer/{dealerId} ( Delete Dealers by identification match with the parameter ) 
  * 1.5 - UPDATE request for http://localhost:8080/dealer ( Update the Dealer informed in  Body section using **dealerId** as key )
  * 1.6 - POST request for http://localhost:8080/dealer ( Save the Dealer informed in  Body section )

* 2 - **Listing** endpoints 
  * 2.0 - GET request for http://localhost:8080/listing  ( Show all Listing registered in the Database )
  * 2.1 - GET request for http://localhost:8080/listing/{listingId} ( Show the Listing details according **listingId** informed and all Listing related )
  * 2.2 - GET request for http://localhost:8080/listing/description/{descriptionVehicle} ( Show all Listing whose **vehicle** atribute match with  **descriptionVehicle** parameter )
  * 2.3 - GET request for http://localhost:8080/listing/state/{stateListing} ( Show all Listing whose **state** atribute match with  **stateListing**  parameter)
  * 2.4 - GET request for http://localhost:8080/listing/dealerid/{dealerId} ( Show all Listing whose **dealerid** atribute match with  **dealerId**  parameter)
  * 2.5 - GET request for http://localhost:8080/listing/dealerid/{dealerId}/state/{stateListing} ( Show all Listing whose **dealerid** atribute match with  **dealerId** and  **state** atribute match with  **stateListing** parameter)
  * 2.6 - POST request for http://localhost:8080/listing ( Save the Dealer informed in  Body section )
  * 2.7 - POST request for http://localhost:8080/listing/overwriting ( Save the Listing informed in Body section removing the oldest registre if limit was reached )
  * 2.8 - UPDATE request for http://localhost:8080/listing ( Update the Listing informed in  Body section using **id** atribute as a key )
  * 2.9 - DELETE request for http://localhost:8080/listing/{listingId} ( Delete Listing using **listingId** as a key) 

## 🚀 Starting Getting Started with Endpoints
## Very Import Tip: Before everything, execute section "Testing environment" Above. "THIS IS ESSENTIAL"

## ⚙️ API RESTFul - Running Examples step by step
* 1 - **Dealer** endpoints
  * 1.1 - Find all Dealer 

## ⚙️ API RESTFul Test- Running Examples step by step
* 1 - **Dealer** endpoints
  * 1.1 - Find all Dealer 

## 📋 API Development - Review Technical Aspect and Improvement Suggestions
* 1 - <Class>
   * 1.1 - Suggest 1
   * 1.2 - Suggest 2
 
## 📋 API Test - Review Technical Aspect and Improvement Suggestions
* 1 - <Class>
   * 1.1 - Suggest 1
   * 1.2 - Suggest 2

## ⚙️ Documentation Swagger
* 9 - Open browser and type: http://localhost:/swagger-ui.html (This url will open a page with and example for API use.

## 🛠️ Building tools

* Eclipse
* Maven

## 📌 Version

* Tags in https://github.com/task-api-restful

## ✒️ Author

* **Developer** - //https://github.com/edfcbz

## 📄 License

* NA
7
