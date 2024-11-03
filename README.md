# Backend-Engineering-projects
This repository provides a curated collection of tasks, challenges, and projects designed to help upcoming backend engineers hone their skills and gain practical experience in backend development. Each task includes detailed instructions, database structures, model designs, and API endpoints to implement.


`Task 1: REST API for a Library Management System`

### Objective: 
The goal of this test is to build a RESTful API for a library management system. 
The system should manage books, authors, and users. It should also handle 
borrowing and returning books, with additional features such as role-based 
access control, search, and caching.

### Requirements: 
1. Environment: 
- The solution should use a relational database (e.g., MySQL, PostgreSQL, 
SQLite).

2. Entities: 
Book: 
- id: Integer, primary key 
- isbn: String, required, unique 
- published_date: Date 
- author_id: Foreign key to Author 
- status: Enum [Available, Borrowed], required 
Author: 
- id: Integer, primary key 
- name: String, required 
- bio: Text, optional 
- birthdate: Date, optional 
User: 
- id: Integer, primary key 
- name: String, required 
- email: String, required, unique 
l password: String, required 
l role: Enum [Admin, Librarian, Member], required 
BorrowRecord:
id: Integer, primary key 
- user_id: Foreign key to User 
- book_id: Foreign key to Book 
- borrowed_at: DateTime, required 
- due_at: DateTime, required 
- returned_at: DateTime, optional

### API Endpoints: 
Books: 
- GET /books: Retrieve a list of all books. 
- GET /books/{id}: Retrieve details of a specific book by ID. 
- POST /books: Create a new book (Admin/Librarian only). 
- PUT /books/{id}: Update an existing book by ID (Admin/Librarian only). 
- DELETE /books/{id}: Delete a book by ID (Admin only). 
- POST /books/{id}/borrow: Borrow a book (Member only, if available). 
- POST /books/{id}/return: Return a borrowed book (Member only). 

Authors: 
- GET /authors: Retrieve a list of all authors. 
- GET /authors/{id}: Retrieve details of a specific author by ID. 
- POST /authors: Create a new author (Admin/Librarian only).
- PUT /authors/{id}: Update an existing author by ID (Admin/Librarian only). 
- DELETE /authors/{id}: Delete an author by ID (Admin only). 

Users: 
- GET /users: Retrieve a list of all users (Admin only). 
- GET /users/{id}: Retrieve details of a specific user by ID (Admin only). 
- POST /users: Register a new user. 
- PUT /users/{id}: Update user details (Admin only or self). 
- DELETE /users/{id}: Delete a user by ID (Admin only). 
- POST /login: Authenticate a user and return a jwt/sanctum token. 
BorrowRecords: 
- GET /borrow-records: Retrieve all borrow records (Admin/Librarian only). 
- GET /borrow-records/{id}: Retrieve details of a specific borrow record by 
ID (Admin/Librarian only).

### Additional Requirements:
1. Implement role-based access control (RBAC): 
- Admin: Full access to all resources. 
- Librarian: Can manage books and authors, view borrow records, but 
cannot manage users. 
- Member: Can view books/authors, borrow and return books, and update 
their profile. 
3. Implement search functionality for books by title, author, or ISBN. 
4. Implement pagination for listing books, authors, and borrow records. 
5. Implement input validation for all endpoints. 
6. Implement error handling with appropriate status codes and error 
messages. 
7. Include feature tests for as many API endpoints as possible.
8. Implement rate limiting for API requests to prevent abuse. 

Additional Notes: 
Feel free to use any libraries or tools you're comfortable with.


`Task 2:  News Aggregator API`

### Objective: 
The challenge is to 
build a RESTful API for a news aggregator service that pulls articles from various 
sources and provides endpoints for a frontend application to consume.

### Requirements:
 1. User Authentication:
   - Implement user registration and login endpoints using jwt/Sanctum(for laravel)
   - API token authentication.
   - Include endpoints for user logout and password reset.
 2. Article Management:
   - Create endpoints to fetch articles with support for pagination.
   - Implement search functionality to allow filtering      articles by keyword, date, 
    category, and source.
   - Develop an endpoint for retrieving a single article's details.
 3. User Preferences:
   - Create endpoints to allow users to set and retrieve their preferred news sources, categories, and authors.
   - Implement an endpoint to fetch a personalized news feed based on user preferences.
 4. Data Aggregation:
   - Develop a system to regularly fetch and store articles from at least 3 different news APIs (see the list of data sources below).
   - Implement efficient data storage and indexing for optimized search and retrieval.
 5. API Documentation:
   - Provide comprehensive API documentation using tools like 
    Swagger/OpenAPI

 ### Data Sources:
 Choose at least 3 from the following list:
 1. NewsAPI
 2. 0PenNews
 3. NewsCred
 4. The Guardian
 5. New York Times
 6. BBC News

`Please note that some of these APIs might require registration and authentication 
keys to access the data`


Challenge Guidelines
 1. Backend Project:
 - Develop a RESTful API that fulfills all the above 
requirements.
 Implement proper error handling and validation for all endpoints.
 2. Database Design:
  - Design an efficient database schema to store articles, user data, and 
preferences.
  - Use migrations and seeders for database setup

 3. Data Aggregation:
  - Implement Laravel scheduled commands to regularly fetch and update 
articles from the chosen news APIs.
 - Store the fetched data locally in the database.
  - Ensure that all data filtering and searching operations are performed on 
the local data, not on live API data

 4. Best Practices:
 - Adhere to your choice of framework best practices and coding standards.
  - Incorporate software development principles such as DRY Don't Repeat 
 - Yourself), KISS Keep It Simple, Stupid), and SOLID.
 - Write clean, maintainable, and well-documented code

 5. Testing:
 - Write unit and feature tests for your API endpoints and core functionalities.
 - Aim for good test coverage of your codebase

 6. Performance:
 - Implement caching strategies where appropriate to optimize API 
  performance.
 - Consider implementing rate limiting for API endpoints.

  7. Security:
  - Ensure proper security measures are in place, including protection against 
common vulnerabilities (e.g., SQL injection, XSS).
 - Implement proper authentication and authorization checks for all protected 
routes


`Task 3: Automated Email Noti cation System withCronJobs`

### Objective:
 Build a system that allows users to schedule automated email
 notifications to be sent at a future date using cron jobs.
 Thesystem will:
 - Allowuserstoregister/login/logout.
 - Enableusers to schedule email noti cations.
 - Setupacronjobtosendemailsatthescheduledtime.
 - Manageemailsendingstatus andretries for failed attempts

 The system will:
 - Allowuserstoregister/login/logout.
 - Enableusers to schedule email noti cations.
 - Setupacronjobtosendemailsatthescheduledtime.
 - Manageemailsendingstatus andretries for failed attempts.

 Requirements:
 1. User Authentication:
 - Implement user registration and login functionality
 using sessions.
 - Onlylogged-in users can schedule email noti cations.
 - Use OOP for user management(e.g.,Userclass with
 methods like register(), login(), logout()).

 2. Email Scheduling:
 - Userscanscheduleanemailbyentering:
 - Emailrecipient.
 - Subject andbodyoftheemail.
 - Dateandtimeforsending.
 - Validate input (e.g., correct email format, future date
 for sending).
 - Storethescheduled emails in the database with the
 status (pending, sent, or failed).
 - UseOOPforemailmanagement(e.g., Email class with
 methods like scheduleEmail(), sendEmail()).

 3. Cron Job:
 - Write a script that will be triggered by a cron job.
 This script will:
- Check the database for any emails marked as
 pending where the scheduled time has passed.
 - Send the email using SMTP or an
 external email service like mailtrap etc.
 - Update the email status to sent or failed in the
 database
 - Implementretries for failed email attempts (e.g., retry
 3 times before marking as failed).

 4. Database Design:
 - Tables: users, scheduled_emails
 - Fields in scheduled_emails: recipient_email, subject,
 body, scheduled_time, status, attempts.

 5. CodeStructure:
 - FollowOOPprinciples and create classes such as:
 - User:for managing user authentication.
 - Email: for managing email scheduling and
 sending.
 - Organize the project using the MVC structure:
 - models/: contains the class de nitions.
 - controllers/: processes user input and handles
 logic.
 - views/: handles the presentation layer (e.g., HTML
 forms).
 - con g/:forcon gurationsettings like database
 connection.
 - cron/: contains the cron job script for checking
 and sending scheduled emails.

 6. Cron Job Setup:
 - The cron job should run every minute(oraspreferred)
 to check the database for pending emails.

 7. Additional Requirements:
 - Propererror handling, especially for email sending
 failures.
 - Form validation for all user inputs.
- Use sessions forlogin/logout functionality.
 - Clear, well-organized file structure.

 Important Criteria:
 - Effective use of OOP principles and clean code structure.
 - Implementation and scheduling of cron jobs for email
 sending.
 - Error handling and retry mechanism for failed email sends.
 - Form validation and database interaction.
 - Clear and concise documentation on setting up and running
 the project

 `Task 4: Travel Agency API`

 ### Task description below:
Glossary
Travel is the main unit of the project: it contains all the necessary information, like the number of days, the images, title, etc. An example is Japan: road to Wonder or Norway: the land of the ICE; Tour is a specific dates-range of a travel with its own price and details. Japan: road to Wonder may have a tour from 10 to 27 May at €1899, another one from 10 to 15 September at €669 etc. At the end, you will book a tour, not a travel.

#### Goals at the end, the project should have: 
A private (admin) endpoint to create new users. If you want, this could also be an artisan command, as you like. It will mainly be used to generate users for this exercise; A private (admin) endpoint to create new travels; A private (admin) endpoint to create new tours for a travel; A private (editor) endpoint to update a travel; A public (no auth) endpoint to get a list of paginated travels. It must return only public travels; A public (no auth) endpoint to get a list of paginated tours by the travel slug (e.g. all the tours of the travel foo-bar). Users can filter (search) the results by priceFrom, priceTo, dateFrom (from that startingDate) and dateTo (until that startingDate). User can sort the list by price asc and desc. They will always be sorted, after every additional user-provided filter, by startingDate asc.

>### Models

****Users:****
- ID
- Email
- Password

Roles (M2M relationship)

***Roles***
- ID
- Name

***Travels:***
- ID
- Is Public (bool)
- Slug
- Name
- Description
- Number of days
- Number of nights (virtual, computed by numberOfDays - 1)

***Tours:***
- ID
- Travel ID (M2O relationship)
- Name
- Starting date
- Ending date
- Price (integer, see below)

> ### Note:
Use UUIDs as primary keys instead of incremental IDs, but it's not required for you to use them, although highly appreciated;
Tours prices are integer multiplied by 100: for example, €999 euro will be 99900, but, when returned to Frontends, they will be formatted (99900 / 100);
Every admin user will also have the editor role
Feature tests are a big big plus.