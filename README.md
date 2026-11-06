
## PROG6212-PART3-AphiweGans

## Race. Move. Achieve.

RaceDay is a web-based event management platform developed for the PROG6212 Software Development project. The application is designed to connect event organisers and participants through a central platform where sporting events can be explored, managed and joined.

The platform supports sporting events such as running, walking and cycling events.

## 1. Project Overview

RaceDay provides two main user roles:

Organisers: Manage sporting events and access event-related information.

Participants: Browse available events, view event details and manage their event participation.

The application uses a web-based architecture consisting of an ASP.NET Core MVC frontend, a REST API and a Microsoft SQL Server database. Azure Blob Storage is used for image storage, while Docker is used to containerise the application services.

## 2. Technologies Used

Technology

Purpose

C#

Main programming language

ASP.NET Core MVC

Web application and user interface

ASP.NET Core Web API

Backend API services

Microsoft SQL Server 2022

Database management

Entity Framework Core

Database access and migrations

Azure Blob Storage

Cloud-based image storage

Docker

Application containerisation

Docker Compose

Managing multiple application services

Swagger

API documentation and testing

GitHub Actions

CI/CD workflow

## 3. System Architecture

RaceDay follows a multi-layer application architecture. Each component performs a specific responsibility and communicates with the other components to provide the application's functionality.

Frontend – ASP.NET Core MVC

The MVC application provides the user interface. Users interact with the website through its pages, forms and navigation. It allows organisers and participants to access functionality according to their roles.

Backend – ASP.NET Core Web API

The REST API processes application requests, handles business logic and communicates with the database. The MVC frontend sends requests to the API to retrieve or submit application information.

Database – Microsoft SQL Server

SQL Server stores the application's information, including users, organisers, participants, events, categories, enrolments and results.

Cloud Storage – Azure Blob Storage

Azure Blob Storage is used to store uploaded images separately from the application's database. The application can retrieve and display images using their stored references.

Containerisation – Docker

Docker runs the web application, API and SQL Server as separate services. Docker Compose manages the services and their configuration so that the application can run as an integrated system.

## 4. Main Application Features

4.1 Authentication and User Roles

User registration and login.

Organiser and participant roles.

Role-based navigation.

Access to role-specific application functionality.

4.2 Organiser Interface

The organiser interface provides functionality for managing sporting events.

Features include:

Organiser dashboard.

Event creation and management.

Access to organiser-specific events.

Event image uploads.

Access to event-related enrolment and result information.

4.3 Participant Interface

The participant interface allows users to explore sporting events and manage their participation.

Features include:

Browse available events.

View event information.

Participate in available events through enrolment.

Access personal enrolment information.

View available results.

4.4 Azure Blob Storage

Azure Blob Storage provides cloud storage for application images.

Uploaded images are stored in the configured Azure Blob Storage container, while the application can use their references when displaying images.

Security note: Azure connection strings and access keys must be stored securely in environment variables or configuration settings. They must never be committed to GitHub.

## 5. Database Structure

The application uses Microsoft SQL Server.

The database includes the following tables:

Table

Purpose

Organisers

Stores organiser information

Participants

Stores participant information

Events

Stores sporting event information

Categories

Stores event categories

Enrolments

Stores participant enrolments

Results

Stores event result information

__EFMigrationsHistory

Tracks Entity Framework database migrations

## 6. Running the Project with Docker

## Step 1. Open Docker Desktop
1. Open Docker Desktop on Windows.
2. Wait until Docker Engine is running.
3. Do not proceed until Docker Desktop has finished starting.

## Step 2. Open Windows PowerShell
Copy and paste:
cd "C:\Users\Student\Downloads\RaceDay_Part3_Added_To_Part2\RaceDay_Part2_Final"


## Step 3. Check your Docker configuration
Run:
docker compose config --quiet


If it returns to the prompt without an error, the configuration is valid.

## Step 4. Start RaceDay
Run:
docker compose up --build -d


This builds the application images if necessary and starts the configured services in the background.
Expected services
- raceday-db — SQL Server
- raceday-api — Backend API
- raceday-web — Website
  
## Step 5. Check whether everything is running
Run:
docker ps


You should see these three containers:
Container	Port
raceday-web	8080
raceday-api	8081
raceday-db	14333

SQL Server should ideally show healthy.

## Step 6. Open your website
RaceDay website
http://localhost:8080
  Open RaceDay 
API Swagger documentation

http://localhost:8081/swagger
Open Swagger
Important commands to keep
Task	PowerShell command
Start project	docker compose up -d
Build and start	docker compose up --build -d
Check containers	docker ps
View logs	docker compose logs --tail=100
View API logs	docker compose logs --tail=100 raceday-api
Stop project	docker compose stop
Start existing containers	docker compose start

## 7. API Documentation

RaceDay provides Swagger documentation for exploring and testing available API endpoints.

After starting the application, open:

http://localhost:8080?utm_source=chatgpt.com

Swagger provides an interface for viewing the API operations and testing supported requests.

## 8. Continuous Integration and Deployment

The project contains a GitHub Actions workflow:

.github/workflows/dotnet-ci.yml

The workflow is intended to support automated project validation through GitHub Actions.

The successful execution of the workflow should be checked in the repository's Actions tab. The presence of the workflow file alone does not confirm that the CI/CD pipeline has passed.

## 9. Security Considerations

The project uses several security-related practices:

Authentication for application users.

Role-based access to application functionality.

Password hashing rather than storing plain-text passwords.

Secure handling of Azure Storage credentials.

Database access through the backend API.

Environment-based configuration for sensitive settings.

Actual security controls should be verified against the implemented application before submission.

## 10. Project Structure

The solution contains the following main application projects:

Project

Responsibility

RaceDay.API

Backend REST API

RaceDay.Web

ASP.NET Core MVC frontend

RaceDay.Contracts

Shared application contracts

RaceDay.Tests

Automated tests

The solution also contains Docker configuration, environment configuration and GitHub Actions workflow files.

## 11. Testing and Verification

The application can be checked using the following services:

Website: http://localhost:8080

Swagger: http://localhost:8081/swagger

Docker containers: docker ps

Docker Compose validation: docker compose config --quiet

Additional functional testing should cover authentication, role-based navigation, event management, participant enrolment, image uploads and database operations.

## 12. Conclusion

RaceDay demonstrates the development of a web-based sporting event management platform using modern software development technologies.

By combining ASP.NET Core MVC, REST API services, SQL Server, Azure Blob Storage and Docker, the project brings together application development, database management, cloud storage and containerisation in one integrated solution.

## RaceDay – Race. Move. Achieve.
