# This repository has a RESTFul API for Dealer and Listing entities

This project implements the use, test and log functionalities of the RESTFull API for Dealer and Listing entities, with supports for basic and customized CRUD operations. With different sections, this document define all details of project and how use it. If you have any question about topics below, let me know by email informed in boton of this document. Thank you !

## 📋 Business
* 1 - **Requirements**
  * 1.1 - **Listing** - A vehicle advertisement. Listing can be in one of two possible states: **published** or **draft** (available or not online)</br>
           * 1.1.1 - **Atributes** id: uuid, dealerId: uuid, vehicle: string, price: number, createdAt: date, state: draft/published 
  * 1.2 - **Car Dealer** - An owner of the advertisement</br>
           * 1.2.1 - **Atributes** id: uuid, name: String</br>
           * 1.2.2 - **Tier Limit** A number of published listings a dealer can have online </br>
  * 1.3 - **Logs**
  * 1.4 - **Exception handling**
  * 1.5 - **Documentation**
  * 1.6 - **Tests**

* 2 - **Functionalities**
  * 2.1 - **Listing:** Create, update, delete, find all, find by Id, find by Vehicle description, find by dealer id and state, find by state, publish*, publish** unpublishin the oldest.
  
  * 2.1 - **Car Dealer:** Create, update, delete, find all, find by id, find by id and state, find by dealer name.  

* 3 - **Rules**
  * 3.1 - **Car Dealer** - Must have the maximum number of published Listings 
  * 3.2 - **Listing** - The quantity published is limited, according Dealer setting. During the update the system should check and throw an exception if the limit has been reached as well offer another endpoint during update process as option to replaces the oldest Listing

## ⚙️ Main Technologies
* 1 - **String** Boot, Security and Data
* 2 - **Swagger** API Documentation
* 3 - **Dozer** Class converter
* 4 - **HATEAOS** Supports for RESTFul API 
* 5 - **Jackson** Allows request and response in xml, yaml, json format
* 6 - **JUnit** Test Class in Java Language
* 7 - **Mockito** Offers a library with different methods for performing and validating tests
* 8 - **REST-Assured** API for building tests and validating results
* 9 - **Hamcrast** API for validating REST services 

## ⚙️ Architecture ( MVC Pattern )
This project was developed using the best practices in API RESTFUll development. The solution's layers are listed and described below
* 1 - **Controller** In addition to implementing the endpoints for the services provided by the entity, this layer is responsible for converting the requests made in XML, JSON and YAML format to the format accepted by the backend and also converting responses to the format desired by the API user. 
* 2 - **ServiceVO** Responsible for converting VO class objects to entity classes recognized by the business layer. The VO layer implementation allows modifying the attributes of the inner classes for the user consuming the API. This mapping increases the security of the application by hiding the real attributes of the business classes.
* 3 - **ServiceBO** This layer is accountable for business rules before the operations with the database. Other BO service classes can by used in ths layer. 
* 4 - **JWT** Authentication by token

## ⚙️ UML Diagrams (Simplified)
* 1 - **Class Diagram**

![image](https://user-images.githubusercontent.com/63114961/163382563-3935977b-05bf-430b-a3ab-93b65e12166b.png)

* 2 - **Sequence Diagram**

 ![image](https://user-images.githubusercontent.com/63114961/163385585-6979664b-fffd-4f64-87a0-c976496f4161.png)
 
 * 3 - **Class Test Diagram**
 
![image](https://user-images.githubusercontent.com/63114961/163567713-91ee2b81-a12a-44a0-a600-311e0519853e.png)



## 🛠️ Tools Technical Requirements ( Other can be used according Developer wish )

* 1 - MySQL Server: Version 8.0.19
* 2 - Java 11
* 3 - Eclipse: Version 2020-06 (4.16.0) Build id: 20200615-1200
* 4 - HeidiSQL as SQL client 64 bits: Version 11.0.0.5919 Build 2020-03-17 17:05:04
* 5 - Postman as http request tool: Version 9.16.0

## 🚀 Starting Database and Environment
Fellow the below step for run the project

## 🔧 Development Environment Setup - DATABASE
* 1 - Download in https://github.com/edfcbz/task-api-rest-spring-360agency-test **task-api-rest-360agency.rar** file and unzip it.
* 2 - Install and Run the MySQL Server (Default port)
* 3 - Install and Run the HeidiSQL
  * 3.1 - In HeidiSQL run **CreatingDatabase360agency.sql** and **InsertDataTestInTables.sql** files. These files are located in task-api-rest-360agency\src\main\resources\files folder. For it select: File -> Load SQL file -> Press SQL Execute (Blue Icon), this action will create the SCHEMA and insert basic data into tables. 
  * 3.2 - After prior step refresh environmet pressing F5 key or icon green (Refresh)
  * 3.3 - Verify if schema was created and tables has data 

## 🔧 Development Environment Setup - DEVELOPMENT

* 1 - Run Eclipse and Import the project as "Existing Maven Project" option
* 2 - In Eclipse menu select Project -> Clean
* 3 - Open package br.com.edfcbz, locate **Statup.java** file and run it as Java Application. The TomCat server will run at 8080 port
  * 3.1 - Tips: If the Eclipse console show the message "Caused by: java.net.BindException: Address already in use: bind", means that another process is running at the 8080 port, so finalize the service in 8080 port as showed, if not critical for you
  * 3.2 - Run CMD as Administrator and type de command line: C:\>**netstat -a -n -o | findstr :8080** (This command will show a line as:
          ***TCP 0.0.0.0:8080 0.0.0.0:0 LISTENING 8457** (In this example 8457 is the PID process)
  * 3.3 - Run CMD command line as Administrator: C:\>**taskKill.exe /F /PID 8457** ( This command will show a line as: 
          ***SUCCESS: The process with PID 8457 was terminated.** ( Or similar message )
  * 3.4 - Execute 3.1 step again

## ⚙️ Testing environment
* 1 - Requesting a token (Security Layer)
  * 1.1 - Run Postman
  * 1.2 - Select a POST request and type http://localhost:8080/auth/signin
  * 1.3 - In Body section type: {
                          "username":"leandro",
                          "password":"admin123"
                        }
  * 1.4 - Select SEND button (You will receive a message with a token as below)
  ![image](https://user-images.githubusercontent.com/63114961/163141178-e52010dc-74a7-44c4-9e02-ce4680aafaf5.png)

  * 1.5 - Copy the token returned without ""

* 2 - Requesting a TomCat service
  * 2.0 - Select a GET request and type http://localhost:8080
  * 2.1 - In Header section create or modify a  **Authorization** key with value: Bearer <paste here token received in step 1.3>. Tip: There is just one empty space between Bearer word and token
  * 2.2 - Select SEND button. You will receive a list with all services available, as showed in image below. This is a good news, your environment is on...

![image](https://user-images.githubusercontent.com/63114961/163140854-fb7691cd-cd45-412b-8c78-c5fd09df6046.png)


## ⚙️ API RESTFul - Endpoints list and general informations
* 1 - **Dealer** endpoints
  * 1.1 - **GET** request for http://localhost:8080/dealer ( Show all Dealer registered in the Database )
  * 1.2 - **GET** request for http://localhost:8080/dealer/{dealerId} ( Show the Dealer details according **dealerId** informed and all Listing related )
  * 1.3 - **GET** request for http://localhost:8080/dealer/{dealerId}/{listingState} ( Show the Dealer by dealerId and Listing registered by listingState )
  * 1.4 - **GET** request for http://localhost:8080/dealer/name/{dealerName} ( Lists all dealers whose names match with the parameter, fully or not ) 
  * 1.5 - **POST** request for http://localhost:8080/dealer ( Save the Dealer informed in  Body section )
  * 1.6 - **PUT** request for http://localhost:8080/dealer ( Update the Dealer informed in  Body section using **dealerId** as key )
  * 1.7 - **DELETE** request for http://localhost:8080/dealer/{dealerId} ( Delete Dealers by identification match with the parameter ) 


* 2 - **Listing** endpoints 
  * 2.1 - **GET** request for http://localhost:8080/listing  ( Show all Listing registered in the Database )
  * 2.2 - **GET** request for http://localhost:8080/listing/{listingId} ( Show the all Listing details according **listingId** informed )
  * 2.3 - **GET** request for http://localhost:8080/listing/description/{descriptionVehicle} ( Show all Listing whose **vehicle** atribute match with  **descriptionVehicle** parameter. This endpoint is useful for find vehicle by description complete or not. )
  * 2.4 - **GET** request for http://localhost:8080/listing/state/{stateListing} ( Show all Listing whose **state** atribute match with  **stateListing**  parameter)
  * 2.5 - **GET** request for http://localhost:8080/listing/dealerid/{dealerId} ( Show all Listing whose **dealerid** atribute match with  **dealerId**  parameter)
  * 2.6 - **GET** request for http://localhost:8080/listing/dealerid/{dealerId}/state/{stateListing} ( Show all Listing whose **dealerid** atribute match with  **dealerId** and  **state** atribute match with  **stateListing** parameter)
  * 2.7 - **POST** request for http://localhost:8080/listing ( Save the Dealer informed in  Body section. **Details in API RESTFul - Running Examples** below)
  * 2.8 - **POST** request for http://localhost:8080/listing/overwriting ( Save the Listing informed in Body section removing the oldest registre if limit was reached )
  * 2.9 - **PUT** request for http://localhost:8080/listing ( Update the Listing informed in  Body section using **id** atribute as a key )
  * 2.10 - **DELETE** request for http://localhost:8080/listing/{listingId} ( Delete Listing using **listingId** as a key) 

## 🚀 Starting JUnit Test Class
## VERY IMPORTANT Before everything, execute section "Testing environment" Above. "THIS IS ESSENTIAL"

* 1 - **(Default OPTION)** Access the Database SCHEMA and remove all informations using the command SQL below. (Using HeidiSQL Tool)
  * 1.1 - Clean Listing table: DELETE FROM Listing; 
  * 1.2 - Clean Dealer Table: DELETE FROM Dealer;
  * 1.3 - Execute the file InsertDataTestInTables.sql in Client SQL Tool (This step will create the data tests in Database squema)
  
* 2 - **(Another OPTION)** Creating new database (Using HeidiSQL Tool)
  * 2.1 - Remove the Database schema created before
  * 2.2 - Execute the SQL file "CreatingDatabase360agency.sql" in Client SQL Tool (This step will create the data tests in Database schema) 
  * 2.4 - Execute the SQL file "InsertDataTestInTables.sql" in Client SQL Tool (This step will create data in Schema Tables)
* 3 - Run the **Sturtup.java** class as java application. This file is located in br.com.edfcbz project package or repeat the "Testing environment" section 

## ⚙️ API RESTFul - Running Examples
* 1 - **Dealer** endpoints 
  * 1.1 - Request type **GET** http://localhost:8080/dealer/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd (This endpoint return Dealer details and all Listing related. See image below for details)

![image](https://user-images.githubusercontent.com/63114961/163675037-9894b3ef-c1b2-4d02-b137-061e75f36281.png)</br>

  * 1.2 - Resquet type **GET** http://localhost:8080/dealer/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd/**draft** or /**published** (This endpoint return a specific Dealer using dealerId and Listing by state. In this case **draft**  ( See images below )
  
![image](https://user-images.githubusercontent.com/63114961/163675139-e3352bbd-4548-4a1c-af42-08056d8d596d.png)

  * 1.3 - Resquet type **GET** http://localhost:8080/dealer/name/dealer 1 (Shows a list af all Dealer which has "dealer 1" inside name) ( See images below )

![image](https://user-images.githubusercontent.com/63114961/163675216-805ff0b2-f8dd-4b69-b49d-6e8e0e00649c.png)

  * 1.4 - Resquet type **POST** http://localhost:8080/dealer (Will add a new Dealer registry in Database, before add the personal information in body section as below ) 
  
![image](https://user-images.githubusercontent.com/63114961/163675433-e92248c5-58d7-49b7-a191-f7dc042e6c38.png)</br>
The API will return the Dealer created (See Image below for details)

![image](https://user-images.githubusercontent.com/63114961/163675480-5b04d518-40b0-442c-b018-571504967319.png)</br>
Verify the correct behavior sending a GET request findById as 1.1 Step Above, bus informing the id returned in 1.4 step above too. The result will be similar like below  image

![image](https://user-images.githubusercontent.com/63114961/163675613-482bce0d-e4d3-4a98-a627-7ec268bd0a2e.png)

  * 1.5 - Resquet type **PUT** http://localhost:8080/dealer  (Will update the Dealer information registred in Database, before add the personal information in body section as below )
  
  ![image](https://user-images.githubusercontent.com/63114961/163675694-d3e5ca50-515b-4210-8217-0498e5ba10cf.png)</br>
This operation will update the Dealer name and Limit os Listing state as published. The update return is showed in image below for details

![image](https://user-images.githubusercontent.com/63114961/163675765-e6be55ab-b47e-4eae-b971-b249e82646a6.png)</br>
The Dealer name and Limit Listing as published were modified

Request DELETE http://localhost:8080/dealer/{dealerId} (This endpoint will remove the Dealer if doesn't have Listing. If has, the operation will fail and API will return an Exception. See details below )</br>
![image](https://user-images.githubusercontent.com/63114961/163677242-9c2f9984-46d6-4680-9cb0-197692a74dda.png)


* 2 - **Listing** endpoints (Using data of initial setup and the new Dealer added above )
  * 2.1 - Request **GET** http://localhost:8080/listing/dealerid/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd/state/published 
![image](https://user-images.githubusercontent.com/63114961/163650117-35bbb03f-195a-4c62-bb6b-2221722ff156.png)</br>
**BUSINESS REQUIREMENT** This endpoint implements the Business Requirement, searching and returning all Listing of a Dealer and state of them</br>

  * 2.2 - Request **GET** http://localhost:8080/listing (Will show all Listing from database - See image below for details about one of them. 2 Registry from 5)</br>
![image](https://user-images.githubusercontent.com/63114961/163676004-beab6f59-38c3-4b31-b556-a143e1d0bc34.png)</br>

  * 2.3 - Request **POST**  http://localhost:8080/listing (Will add a new Listing for Dealer created in Dealer 1.4 step above. The information about Listing must be in Body section of request as showed in image below )</br>
  ![image](https://user-images.githubusercontent.com/63114961/163676975-a6b8d65c-cac8-4e9a-8b7c-4c8df4a8e2a1.png)</br>

The result will be similar at image below. **As default the Listing state is draft** See the details</br>
![image](https://user-images.githubusercontent.com/63114961/163676993-a31f501c-c0cd-4b8d-99a7-2037cf1be140.png)</nr>

  * 2.4 - Request **PUT** http://localhost:8080/listing  (The endpoint will modify the Listing created in 2.3 step Above. The Listing data must be in body section as below)</br>
![image](https://user-images.githubusercontent.com/63114961/163677115-64002a05-fb8f-4814-9609-e97bbd65fc5f.png)</br>
The API will return the Listing updated. See image below for details</br>
![image](https://user-images.githubusercontent.com/63114961/163677143-2137e8f8-4755-4a65-8069-177232e23c76.png)

  * 2.5 - Request **DELETE** http://localhost:8080/listing/3bed1f91-38ec-48df-86a2-19dd1ac905ce (The API will return 200 as status code)</br>
   

## ⚙️ API RESTFul JUnit Test - Running Examples
As requirement, this project implemented JUnit test class for Dealer and Listing Service. Some tests are descrited below.

* 1 - **The Test Classes** 
  * 1.1 - The class **BaseClassAPITest.java** connect with data base using user named leandro and password admin123 and set the token static variable. Is not necessary running this class individually. It will run automatically on each test  
  * 1.2 - The class **DealerEndpointDifferentMethodologiesTest.java** shows tests for Dealer endpoint using different test methologies, as example.
  * 1.3 - The class **DealerEndpointTest.java** define the RestAssured methodology using given(), When() and Then(). 
  * 1.4 - The class **ListingEndpointTest.java** test different business aspect 
  
* 2 - **Test Classes Path**
  * 2.1 - Path test for Dealer Entity: src/test/java/br/com/edfcbz/endpoint/dealer package (Run file as JUnit test)
  * 2.2 - Path test for Listing Entity: src/test/java/br/com/edfcbz/endpoint/listing package (Run file as JUnit test)

* 3 - **Suite Test**
  * 3.1 -  The **Suite360AgenceTest.java** class will run all test classes from project. Then, go to path src/test/java/br/com/edfcbz/endpoint/suite package (Run file as JUnit test). The final result will look like the image below.</br>  

![image](https://user-images.githubusercontent.com/63114961/163678283-3890d531-1806-4237-86b1-74324688879f.png)

## 📋 API Development - Review Technical. Improvement Suggestions
* **1 ListingServiceBO.java**
   * 1.1 - Method **public Listing update(Listing listing_)**
           *This method need some improvements in logical and structural aspect. Improve the Listing limit test (published)
   * 1.2 - Method **public Listing published(String listingId)**
           *Similar behavior with update methody, it's possible improve the Limit Listing test, creating a new class or method for test it.

* **2 - DealerServiceBO.java**
   * 2.1 - Method **public Dealer update(Dealer _dealer)**
           *This method need improvements during Limit updating. This service not verify the Listing state as published yet ( Known bug )

* **3 - Exception Classes**
   * 3.1 - Generalize and reduce the number of exception classes. It will be important to adopt a handle class that will be accountable for returning the appropriate exception class for each case.

## 📋 LOG - Review Technical and Improvement Suggestions
   * 1.1 - Increase details, adding logged user in the message
   * 1.2 - Currently shown log message on console. Add save-to-file behavior

## 📋 JUnit Test - Review Technical and Improvement Suggestions

**(Functional Test)** Status: Developed
* **1 - ListingEndpointTest.java 
   * 1.1 - Class **DealerEndpointTest.java**
   * 1.2 - Class **ListingEndpointTest,java**
In general, deepen the level of verification of expected results, especially when the return has complex object with objects and list inside. Example: the draft or published Listing of a specific dealer

**(Coverage Test)** Status: Technical debt (Not developed)
**(Unit Test)** Status: Technical debt (Not developed)

## 📋 DevOps - Review Technical, and Improvement Suggestions
Is essential implement the DevOps concept as below:
* 1 - Continuous Development and Continuous Delivery environment CD/CI using tools such as pipeline Jenkins
* 2 - Quality Gate and Sonar To define the developed code acceptance criteria
* 3 - Dockerized environment, for Development, Homologation and Production

## 📋 Technical Debt
Was require the use of the UUID data type as an identifier for the Dealer and Listing entities, however the project used the String type and the **org.hibernate.id.UUIDGenerator** as strategy to generate the primary keys.

## ⚙️ Documentation Swagger
Open browser and type: http://localhost:/swagger-ui.html (This url will open a page with and example for API use.

## 🛠️ Building tools

* Eclipse
* Maven

## 📌 Version

* Tags in **https://github.com/edfcbz/task-api-rest-spring-360agency-test**

## ✒️ Author

* **Developer contact** - edfcbz@gmail.com

## 📄 License

 **NA**
