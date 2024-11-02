# Backend-Engineering-projects
This repository provides a curated collection of tasks, challenges, and projects designed to help upcoming backend engineers hone their skills and gain practical experience in backend development. Each task includes detailed instructions, database structures, model designs, and API endpoints to implement.

REST API for a Library Management System

## Objective: 
The goal of this test is to build a RESTful API for a library management system. 
The system should manage books, authors, and users. It should also handle 
borrowing and returning books, with additional features such as role-based 
access control, search, and caching.

## Requirements: 
1. Environment: 
l The candidate is required to use Laravel for this test. 
l The solution should use a relational database (e.g., MySQL, PostgreSQL, 
SQLite).

2. Entities: 
Book: 
l id: Integer, primary key 
l title: String, required 
l isbn: String, required, unique 
l published_date: Date 
l author_id: Foreign key to Author 
l status: Enum [Available, Borrowed], required 
Author: 
l id: Integer, primary key 
l name: String, required 
l bio: Text, optional 
l birthdate: Date, optional 
User: 
l id: Integer, primary key 
l name: String, required 
l email: String, required, unique 
l password: String, required 
l role: Enum [Admin, Librarian, Member], required 
BorrowRecord:
