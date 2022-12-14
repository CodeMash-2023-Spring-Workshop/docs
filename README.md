# Getting Started with Spring - Workshop

Learn the fundamentals of Spring, build and deploy your first application.

## Runerz Application

The application you will build during this workshop revolves around the domain of tracking physical fitness. In the first
iteration of it we will use it track indoor and outdoor runs.

## Objectives and Outcomes

- Learn how to create a basic Spring Boot application.
- Learn a few of the fundamentals of Spring
- Build a CRUD REST API
- Connect to a database
- Deploy a Spring Boot application into production

## Prerequisites

- Beginner / Intermediate Java experience
- Experience with Java Build Tools (Maven or Gradle)
- Software
  - Java 17 JDK
  - IDE or Text Editor for Java Development
    - [IntelliJ IDEA Ultimate 2022.3](https://www.jetbrains.com/idea/download/)
      - This is what we are using (30 day trail)
      - Community Edition (Has some limitations)
    - Visual Studio Code
    - Spring Tool Suite
  - API Testing Tool (One of the following)
    - [Postman](https://www.postman.com/product/rest-client/)
    - [HTTPie](https://httpie.io/)
    - [curl](https://curl.se/)
  - Docker Desktop (not required)

## Agenda

- Introduction
  - Who are we
  - Spring Office Hours
  - Agenda
    - Workshop Agenda / Sections
    - Prerequisites
      - java -version
      - macOS/Windows/Linux
        - DaShaun show Windows / Linux setup
  - What is Spring?
    - What types of applications can you build with Spring? (Motivation for the workshop)
    - Spring Framework vs Spring Boot
    - Spring.io walkthrough
      - Reference Documentation
      - API Documentation
      - Spring Project Ecosystem
    - Tanzu Developer Center
  - Spring Boot Features
    - Spring Boot Starters (Dependency Management)
    - Auto Configuration
    - Simplified Deployment
  - What are we going to build?
    - Github Repository
    - Source Code + Slides Repo
    - Provide a list of resources (cover this)
- Getting Started
  - start.spring.io
  - Examine pom.xml
    - Spring Boot Starters
    - Dependency Versions
  - Main Application Class
    - @SpringBootApplication annotation
  - How to start the application
    - IDE
    - Maven
    - View the application / browser & command-line
- Core Fundamentals & Features
  - Structuring your code
  - Spring IoC Container / Application Context
  - Spring Beans
  - Dependency Injection
  - Configuration
  - Profiles
  - Actuator
  - Logging
  - DevTools
- Spring Web (MVC)
  - Model View Controller (MVC)
  - Static index.html support
  - Building REST APIs
    - Annotations
    - CRUD REST API
    - API testing (curl/httpie/postman)
    - CORS
  - Data Validation
- Data
  - Java + SQL Databases
  - Spring Data JDBC API
  - Configuring a Datasource
    - H2
    - PostgreSQL
  - Populate a Database
    - DDL Script
    - Programmatically
  - JDBC Template
  - Spring Data
    - Spring Data Modules
    - Spring Boot Starters
  - Spring Data JDBC
    - Dependencies
    - Persistent Entities
    - Repositories
- Spring to Production
  - Uber Jar
  - Containers
  - Native Images using GraalVM
