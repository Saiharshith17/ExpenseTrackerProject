Auth & Expense Management System

Overview

This project is a microservices-based system designed for secure authentication, user management, expense tracking, and integration with OpenAI's LangChain for processing bank transaction messages. The system leverages Kafka for asynchronous messaging, Redis for caching, and Kong API Gateway for secure and scalable API access.

Architecture

The system consists of the following services:

1. Auth Service (JWT Authentication & Authorization)

Handles user authentication using JWT tokens.

Generates access and refresh tokens for users.

Manages authorization for secured endpoints.

Uses Redis for caching authentication data.

2. User Service (User Management)

Handles all user-related requests, such as retrieving user details.

Uses Redis for caching frequently accessed user information.

Communicates with other services via Kafka.

3. Integration Service (OpenAI LangChain Integration)

Converts bank transaction messages into structured JSON data.

Uses OpenAI's LangChain to process transaction details.

Sends the processed data to the Expense Service via Kafka.

4. Expense Service (Expense Tracking)

Handles expense-related operations such as adding and retrieving expenses.

Uses Redis for caching expense data.

Receives processed transactions from Integration Service via Kafka.

API endpoints are managed through Kong API Gateway.

Technologies Used

Frontend: ReactJS, JavaScript, HTML, CSS, Context API

Backend: Java, Spring Boot, Groovy, RESTful API

Database: MySQL, Hibernate

Caching & Messaging: Redis, Kafka

Integration: OpenAI LangChain

Containerization & API Gateway: Docker, Kong

Key Features

Secure Authentication: JWT-based authentication with refresh token support.

Scalability & Performance: Kafka for event-driven communication and Redis for caching.

Bank Transaction Processing: LangChain-powered transaction message parsing.

Expense Management: CRUD operations for user expenses.

API Gateway: Kong for secure and efficient API request handling.

Microservices Communication: Decoupled services integrated through Kafka.

Setup Instructions

Prerequisites

Java 17+

Node.js 16+

Docker

Kafka & Zookeeper

MySQL Database

Redis

Kong API Gateway

Installation Steps

Clone the repository:

git clone <repository_url>
cd auth-expense-management

Start Kafka & Redis:

docker-compose up -d

Set up the MySQL database:

Create a database expense_db.

Update application.properties with database credentials.

Start Auth Service:

cd auth-service
mvn spring-boot:run

Start User Service:

cd user-service
mvn spring-boot:run

Start Integration Service:

cd integration-service
mvn spring-boot:run

Start Expense Service:

cd expense-service
mvn spring-boot:run

Run the frontend:

cd frontend
npm install
npm start

API Endpoints

Service

Endpoint

Method

Description

Auth Service

/auth/login

POST

Authenticate user & return JWT tokens

Auth Service

/auth/refresh-token

POST

Generate new access token using refresh token

User Service

/user/details/{id}

GET

Fetch user details by ID

Expense Service

/expense/add

POST

Add a new expense

Expense Service

/expense/{id}

GET

Retrieve expense details

Integration Service

/integration/process

POST

Process transaction message

Future Enhancements

Implement user role-based access control.

Add automated testing using JUnit & Cypress.

Improve monitoring with Prometheus & Grafana.

Support multi-currency expense tracking.

Contributors

Saiharshith - Lead Developer

License

This project is licensed under the MIT License.
