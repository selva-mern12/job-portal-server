# Job Portal Backend

## Overview
The **Job Portal Backend** is a Node.js and Express-based REST API that provides functionalities for job seekers and employers. It allows users to register, log in, post jobs, apply for jobs, update job listings, and delete job postings.

## Features
- **User Authentication** (Register, Login, JWT-based authentication)
- **Post Job Listings** (Employers can add job details)
- **Retrieve Job Listings** (Get all jobs or specific job details)
- **Update & Delete Jobs** (Modify job postings securely)
- **Apply for Jobs** (Job seekers can apply for jobs)
- **Retrieve Applied Jobs** (See jobs users have applied for)

## Technologies Used
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **SQLite** - Lightweight database
- **JWT** - Authentication & Authorization
- **bcrypt.js** - Password encryption
- **CORS** - Handling cross-origin requests
- **dotenv** - Environment variables

## Installation
### Prerequisites
Ensure you have **Node.js** installed on your machine.

### Steps to Install
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/job-portal-backend.git
   cd job-portal-backend
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Create a `.env` file in the root directory and add:
   ```env
   JWT_SECRET=your_secret_key (use your self)
   ```
4. Start the server:
   ```sh
   npm start
   ```
   The backend will run on `http://localhost:3005/`

## API Endpoints
### **Authentication**
#### Register User
- **Endpoint:** `POST /register`
- **Request Body:**
  ```json
  {
    "username": "selva_1201",
    "email": "selva@example.com",
    "password": "selva@MERN1201" 
  }
  ```
- **Response:**
  ```json
  { "message": "User registered successfully!" }
  ```

#### Login User
- **Endpoint:** `POST /login`
- **Request Body:**
  ```json
  {
    "email": "selva@example.com",
    "password": "selva@MERN1201"
  }
  ```
- **Response:**
  ```json
  {
    "message": "Login successful",
    "user_id": "user123",
    "username": "selva_1201",
    "token": "jwt_token"
  }
  ```

### **Job Management**
#### Post a Job (Authenticated)
- **Endpoint:** `POST /job/add`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Request Body:**
  ```json
  {
    "user_id": "user123",
    "company_name": "Tech Corp",
    "logo_url": "https://logo.com/image.png",
    "job_position": "Software Engineer",
    "monthly_salary": "5000",
    "job_type": "Full-time",
    "remote_office": "Remote",
    "location": "New York, USA",
    "job_description": "Develop web applications...",
    "about_company": "Leading tech company...",
    "skills_required": "JavaScript, React, Node.js",
    "additional_info": "Great work culture."
  }
  ```
- **Response:**
  ```json
  { "message": "Job posted successfully!" }
  ```

#### Get All Jobs
- **Endpoint:** `GET /job/get`
- **Response:**
  ```json
  [
    {
      "job_id": "job123",
      "company_name": "Tech Corp",
      "job_position": "Software Engineer",
      "location": "New York, USA"
    }
  ]
  ```

#### Update a Job (Authenticated)
- **Endpoint:** `PUT /job/update/:id`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Request Body:**
  ```json
  {
    "company_name": "Updated Tech Corp",
    "monthly_salary": "60000"
  }
  ```
- **Response:**
  ```json
  { "message": "Job updated successfully" }
  ```

#### Delete a Job (Authenticated)
- **Endpoint:** `DELETE /job/delete/:id`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Response:**
  ```json
  { "message": "Job deleted successfully" }
  ```

### **Apply for a Job**
#### Apply to a Job (Authenticated)
- **Endpoint:** `POST /job/apply`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Request Body:**
  ```json
  {
    "user_id": "user123",
    "job_id": "job123",
    "company_name": "Tech Corp",
    "logo_url": "https://logo.com/image.png",
    "job_position": "Software Engineer",
    "applied_date": "11-03-2025"
  }
  ```
- **Response:**
  ```json
  { "message": "Job applied successfully!" }
  ```

#### Get Applied Jobs (Authenticated)
- **Endpoint:** `GET /job/applied/:user_id`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Response:**
  ```json
  [
    {
      "apply_id": "apply123",
      "job_position": "Software Engineer",
      "company_name": "Tech Corp",
      "applied_date": "11-03-2025"
    }
  ]
  ```

#### Delete Applied Job (Authenticated)

- **Endpoint:** `DELETE /job/applied/delete/:apply_id`
- **Headers:**
  ```
  Authorization: Bearer <JWT_TOKEN>
  ```
- **Response:**
  ```json
  { "message": "Applied job deleted successfully!" }
  ```

## License
This project is licensed under the **ISC License**.

## Author
Developed by **Selva Job Portal** Team.

