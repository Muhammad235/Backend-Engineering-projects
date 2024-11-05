# Backend-Engineering-Projects
This repository provides a curated collection of tasks, challenges, and projects designed to help upcoming backend engineers hone their skills and gain practical experience in backend development. Each task includes detailed instructions, database structures, model designs, and API endpoints to implement.

## Tasks
- [Task 1: REST API for a Library Management System](#task-1-rest-api-for-a-library-management-system)
- [Task 2: News Aggregator API](#task-2-news-aggregator-api)
- [Task 3: Automated Email Notification System with Cron Jobs](#task-3-automated-email-notification-system-with-cron-jobs)
- [Task 4: Travel Agency API](#task-4-travel-agency-api)

---

## Task 1: REST API for a Library Management System

### Objective
Build a RESTful API for a library management system that manages books, authors, and users. It should also handle borrowing and returning books, with additional features like role-based access control, search, and caching.

### Requirements

1. **Environment**
   - Use a relational database (e.g., MySQL, PostgreSQL, SQLite).

2. **Entities**
   - **Book**
     - `id`: Integer, primary key
     - `isbn`: String, required, unique
     - `published_date`: Date
     - `author_id`: Foreign key to Author
     - `status`: Enum [Available, Borrowed], required
   - **Author**
     - `id`: Integer, primary key
     - `name`: String, required
     - `bio`: Text, optional
     - `birthdate`: Date, optional
   - **User**
     - `id`: Integer, primary key
     - `name`: String, required
     - `email`: String, required, unique
     - `password`: String, required
     - `role`: Enum [Admin, Librarian, Member], required
   - **BorrowRecord**
     - `id`: Integer, primary key
     - `user_id`: Foreign key to User
     - `book_id`: Foreign key to Book
     - `borrowed_at`: DateTime, required
     - `due_at`: DateTime, required
     - `returned_at`: DateTime, optional

3. **API Endpoints**
   - **Books**
     - `GET /books`: Retrieve all books.
     - `GET /books/{id}`: Retrieve specific book by ID.
     - `POST /books`: Create a book (Admin/Librarian).
     - `PUT /books/{id}`: Update a book by ID (Admin/Librarian).
     - `DELETE /books/{id}`: Delete a book by ID (Admin).
     - `POST /books/{id}/borrow`: Borrow a book (Member, if available).
     - `POST /books/{id}/return`: Return a borrowed book (Member).
   - **Authors**
     - Similar CRUD operations for authors.
   - **Users**
     - Admin-only access to view and manage users.
     - `POST /login`: Authenticate and return a JWT/sanctum token.
   - **BorrowRecords**
     - View borrow records (Admin/Librarian).

4. **Additional Requirements**
   - Implement RBAC, search, pagination, validation, error handling, feature tests, and rate limiting.

---

## Task 2: News Aggregator API

### Objective
Build a RESTful API for a news aggregator service that fetches articles from various sources and provides endpoints for a frontend application to consume.

### Requirements

1. **User Authentication**
   - User registration and login with JWT/Sanctum.
   - API token authentication and password reset.

2. **Article Management**
   - Fetch articles with pagination, search/filter by keyword, date, category, and source.

3. **User Preferences**
   - Allow users to set and retrieve preferences (news sources, categories, authors).

4. **Data Aggregation**
   - Fetch articles from at least 3 APIs (e.g., NewsAPI, The Guardian, BBC News) and store locally.

5. **API Documentation**
   - Provide documentation using Swagger/OpenAPI.

---

## Task 3: Automated Email Notification System with Cron Jobs

### Objective
Build a system that allows users to schedule automated email notifications to be sent at a future date using cron jobs.

### Requirements

1. **User Authentication**
   - Implement registration and login with sessions.
   - Logged-in users can schedule email notifications.

2. **Email Scheduling**
   - Allow users to schedule emails with recipient, subject, body, and send date/time.
   - Use OOP principles (e.g., `Email` class with `scheduleEmail()`, `sendEmail()` methods).

3. **Cron Job**
   - Check for pending emails and send them at the scheduled time using SMTP.
   - Implement retries for failed email attempts.

4. **Database Design**
   - Tables: `users`, `scheduled_emails` with fields like recipient_email, subject, body, scheduled_time, status, attempts.

5. **Code Structure**
   - Use an MVC structure for organizing the code.

---

## Task 4: Travel Agency API

### Objective
Develop a RESTful API for managing travels and tours. Users can browse public travels and book tours.

### Requirements

1. **Models**
   - **User**
     - Fields: `ID`, `Email`, `Password`
   - **Roles** (Many-to-Many with Users)
   - **Travels**
     - Fields: `ID`, `IsPublic`, `Slug`, `Name`, `Description`, `NumberOfDays`
   - **Tours**
     - Fields: `ID`, `TravelID`, `Name`, `StartingDate`, `EndingDate`, `Price`

2. **Endpoints**
   - Private (admin) endpoint for creating travels, tours, and users.
   - Public endpoint for browsing travels and tours with filtering and sorting options.

3. **Note**
   - Use UUIDs as primary keys if possible.
   - Use integer values for tour prices (e.g., 99900 for €999.00).
