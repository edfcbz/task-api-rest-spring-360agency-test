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

### 🔧 Development Environment Setup - DATABASE

* 1 - Install and Run the MySQL Server (Default port)
* 3 - Install and Run the HeidiSQL
  * 3.1 - Create a new database named task-api-rest-360agency
  * 3.2 - User: root password: admin123 
* 4 - Run DB_APIREST.sql by MySQL Workbench (This step will create the SCHEMA and will insert basic data into tables) 

### 🔧 Development Environment Setup - DEVELOPMENT

* 5 - Import the project on your IDE (Ex.: Eclipse)
* 6 - Locate, Config and Run the file JOOQConfig.java at path /task-api-restful/src/main/java/br/com/edfcbz/api/app/JOOQConfig.java (Project source)
* 7 - Running java class \src\main\java\br\com\edfcbz\api\Startup.java (Will start an Application Server)

## ⚙️ Testing environment
* 8 - Open browser and type: http://localhost:8080/store (This url will list all store registered in store table.

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
