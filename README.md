# This repository has a RESTFul API for Dealer and Listing entities

This project implements the use of a RESTFull API for Dealer and his/her Listing, inclusing supports the Controller Class for a complete and customized CRUD operations

## 🚀 Starting

Download the complete project by GitHub option

Search **Implantation** about project setup on development environment.

### 📋 Requisites

* 1 - MySQL Database (SGBD Tool)
* 2 - Java 11
* 3 - IDE Development. The project was developed Eclipse Version: 2020-06 (4.16.0) Build id: 20200615-1200
* 4 - The source code from https://github.com/edfcbz/task-api-rest-spring-360agency-test
* 5 - Database client as MySql Workbench. The project choose HeidiSQL 64 bits Version 11.0.0.5919 Build 2020-03-17 17:05:04
* 6 - Http request tool as Postman  

### 🔧 Development Environment Setup - DATABASE

* 1 - Install and Run the MySQL Server (Default port)
* 3 - Install and Run the HeidiSQL
  * 3.1 - In HeidiSQL run CreateDataBaseAndData.sql file (This step will create the SCHEMA and will insert basic data into tables). For it select: File -> Load SQL file -> Press SQL Execute (Blue Icon)
  * 3.2 - After prior step refresh environmet F5 key or press icon green (Refresh)
  * 3.3 - Verify if squema was created and tables has data 

### 🔧 Development Environment Setup - DEVELOPMENT

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
  {"username": "leandro","token": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJsZWFuZHJvIiwicm9sZXMiOlsiQURNSU4iLCJNQU5BR0VSIl0sImlhdCI6MTY0OTgxMTExMSwiZXhwIjoxNjQ5ODE0NzExfQ.PFenUMoOdV1da7c01APm7WN7VbX4xsngsZlbujHco4Q"}                        
  * 1.4 - Copy the token returned without ""

* 2 - Requesting a TomCat service
  * 1.0 - Select a GET request and type http://localhost:8080
  * 1.1 - In Header section create a new Authorization key with value: Bearer <paste here token received in step 1.3>. Tip: There is just one empty space between Bearer and token
  * 1.2 - Select SEND button. You will receive all a list with services available. This message is like this below:
  {
    "_links": {
        "dealers": {
            "href": "http://localhost:8080/dealers{?page,size,sort}",
            "templated": true
        },
        "users": {
            "href": "http://localhost:8080/users{?page,size,sort}",
            "templated": true
        },
        "listings": {
            "href": "http://localhost:8080/listings{?page,size,sort}",
            "templated": true
        },
        "profile": {
            "href": "http://localhost:8080/profile"
        }
    }
}

### Features

- [x] Cadastro de usuário
- [x] Cadastro de cliente
- [ ] Cadastro de produtos

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
