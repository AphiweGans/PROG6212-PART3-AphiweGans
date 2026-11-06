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

Prerequisites

Before running RaceDay, ensure that you have installed:

Docker Desktop.

Docker Compose (included with current Docker Desktop installations).

Git, if cloning the repository.

A compatible Windows, macOS or Linux environment.

Step 1: Clone the repository

git clone YOUR_GITHUB_REPOSITORY_URL

Navigate into the project directory containing the Docker Compose file.

Step 2: Configure environment variables

Create or configure the .env file required by the Docker Compose configuration.

Add the required SQL Server password:

MSSQL_SA_PASSWORD=YOUR_SECURE_PASSWORD

Configure the Azure Blob Storage connection string using your own Azure Storage account credentials.

Do not commit the .env file or expose your credentials.

Step 3: Start the application

Run:

docker compose up --build

Docker Compose builds and starts the configured application services.

Step 4: Access the application

Once the containers are running, access the services using the following addresses:

Service

Address

RaceDay Website

http://localhost:8080

API Swagger Documentation

http://localhost:8081/swagger

SQL Server

localhost, port 14333

Step 5: Stop the application

To stop the running containers, use:

docker compose stop

To start the existing containers again:

docker compose start

Database warning: Avoid using docker compose down -v because it removes associated Docker volumes and can result in database data loss.

## 7. API Documentation

RaceDay provides Swagger documentation for exploring and testing available API endpoints.

After starting the application, open:

http://localhost:8081/swagger

Swagger provides an interface for viewing the API operations and testing supported requests.
