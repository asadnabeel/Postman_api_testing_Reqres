# API Testing Project for Reqres.in

This project focuses on comprehensive API testing of the [Reqres.in](https://reqres.in/) sample API using Postman. Over **50 test cases** were implemented to validate endpoints, response schemas, performance, and data integrity. Below is an overview of the tests, setup instructions, and details about the Postman collection.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Postman Collection](#postman-collection)
- [Setup Instructions](#setup-instructions)
- [Test Cases by Endpoint](#test-cases-by-endpoint)
- [Contribution Guidelines](#contribution-guidelines)

---

## Project Overview
Reqres.in is a mock API designed for testing and prototyping. This project validates its endpoints to ensure:
- Correct HTTP status codes.
- Response time performance.
- Data consistency and schema validation.
- Absence of sensitive information.
- Error handling for invalid requests.

---

## Features
- **50+ Test Cases**: Covering CRUD operations, authentication, pagination, and edge cases.
- **Postman Collection**: Pre-configured requests and automated test scripts.
- **Environment Variables**: Uses `{{base_url}}` for flexibility (default: `https://reqres.in`).
- **Performance Checks**: Response time validations (e.g., `< 2000ms`).
- **Schema Validation**: Ensures JSON structure matches expectations.

---

## Postman Collection
The collection includes all requests and test scripts.  
**Download**: [ReqRes.in.postman_collection.json](/ReqRes.in.postman_collection.json)  

### Import Instructions:
1. Open Postman.
2. Click **Import** → Upload the provided JSON file.
3. Set the `base_url` environment variable to `https://reqres.in` (if not auto-populated).

---

## Setup Instructions
1. **Install Postman**: Download from [Postman's official site](https://www.postman.com/).
2. **Import Collection**: Follow the steps above.
3. **Run Tests**:
   - Open a request in the collection.
   - Click **Send** → View test results in the **Test Results** tab.

---

## Test Cases by Endpoint
Below are key tests performed for each endpoint, aligned with the order on Reqres.in:

### 1. List Users (`GET /api/users`)
- Status code: `200 OK`.
- Response time `< 2000ms`.
- Verify pagination data (`page`, `per_page`, `data[0].id`).

### 2. Single User (`GET /api/users/{id}`)
- Status code: `200 OK`.
- Validate fetched user matches requested ID.
- Check presence of `id`, `email`, `first_name`, `last_name`.
- Ensure email format is valid (e.g., `user@domain.com`).
- Validate schema (data types, no sensitive fields like `password`).

### 3. User Not Found (`GET /api/users/23`)
- Status code: `404 Not Found`.
- Empty response body.

### 4. List Resources (`GET /api/unknown`)
- Status code: `200 OK`.
- Validate resource data (e.g., `id`, `name`, `year`).

### 5. Create User (`POST /api/users`)
- Status code: `201 Created`.
- Confirm response contains `name` and `job` from the request.

### 6. Update User (`PUT/PATCH /api/users/2`)
- Status code: `200 OK`.
- Verify updated fields (e.g., `name`, `email`).
- Response time `< 1000ms`.

### 7. Delete User (`DELETE /api/users/2`)
- Status code: `204 No Content`.
- Validate empty response body.

### 8. Register & Login (`POST /api/register`, `POST /api/login`)
- **Success**: Status `200 OK` with valid `token`.
- **Failure**: Status `400 Bad Request` with error message (e.g., missing password).

### 9. Delayed Response (`GET /api/users?delay=3`)
- Status code: `200 OK`.
- Response time `> 1000ms` (validates intentional delay).

---

## Contribution Guidelines
1. **Fork the repository**.
2. Add/modify tests in the Postman collection.
3. Update the README if endpoints or validations change.
4. Submit a pull request with a clear description.

---

**License**: MIT  
**Maintainer**: Muhammad Asad Nabeel  
**Last Updated**: 16 March 2025