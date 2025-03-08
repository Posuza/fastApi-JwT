# FastAPI JWT Authentication Project

A RESTful API built with FastAPI that implements JWT authentication for blog management. Users can create accounts, authenticate, and manage blog posts.

## Features

- User registration and authentication with JWT
- Blog post creation and management
- Relationship between users and blog posts
- SQLite database with SQLAlchemy ORM
- Password hashing with bcrypt

## Tech Stack

- FastAPI - Modern, fast web framework for building APIs
- SQLAlchemy - SQL toolkit and ORM
- Pydantic - Data validation and settings management
- Passlib & Bcrypt - Password hashing
- Python-jose - JWT token handling
- SQLite - Lightweight database

## Installation

1. Clone the repository:
  ```bash
    git clone https://github.com/yourusername/fastapi-jwt.git
    cd fastapi-jwt
  ```

Create a virtual environment:
    ```python
        python -m venv venv
        source venv/bin/activate
        # On Windows: venv\Scripts\activate
    ```
### Install dependencies:
    - pip install -r requirements.txt
    - Copy
    - Insert

### Running the Application
 - Start the server with uvicorn:
    ```python
      uvicorn main:app --reload
    ```
  -The API will be available at http://localhost:8000

### API Documentation
  . Once the application is running, you can access the interactive API documentation at:
    - Swagger UI: http://localhost:8000/docs
    - ReDoc: http://localhost:8000/redoc
#### API Endpoints
 - Authentication
    - POST /login - Authenticate user and get JWT token
    - Users
    - POST /user/ - Create a new user
    - GET /user/{id} - Get user details by ID
    - Blogs
    - GET /blog/ - Get all blogs
    - POST /blog/ - Create a new blog (requires authentication)
    - GET /blog/{id} - Get blog by ID
    - DELETE /blog/{id} - Delete blog by ID (requires authentication)
    - PUT /blog/{id} - Update blog by ID (requires authentication)

### Project Structure

    ```python
      fastapi-jwt/
      ├── blog/
      │   ├── database.py - Database connection and session management
      │   ├── models.py - SQLAlchemy ORM models
      │   ├── schemas.py - Pydantic models for request/response validation
      │   └── routers/
      │       ├── authentication.py - Login and token generation
      │       ├── blog.py - Blog CRUD operations
      │       └── user.py - User management
      ├── main.py - Application entry point
      └── requirements.txt - Project dependencies
    ```

### Authentication Flow
  - Register a new user via POST /user/
  - Obtain JWT token via POST /login
  - Include the token in the Authorization header for protected endpoints:
  - Authorization: Bearer {your_token}


### Example Usage
  - Creating a User
  ```python 
    curl -X 'POST' \
      'http://localhost:8000/user/' \
      -H 'Content-Type: application/json' \
      -d '{
      "name": "John Doe",
      "email": "john@example.com",
      "password": "securepassword"
    }'
  ```

#### Authenticating
  ```python 
      curl -X 'POST' \
        'http://localhost:8000/login' \
        -H 'Content-Type: application/json' \
        -d '{
        "username": "john@example.com",
        "password": "securepassword"
      }'
  ```

#### Creating a Blog Post (Authenticated)

  ```python 
      curl -X 'POST' \
        'http://localhost:8000/blog/' \
        -H 'Authorization: Bearer {your_token}' \
        -H 'Content-Type: application/json' \
        -d '{
        "title": "My First Blog",
        "body": "This is the content of my first blog post."
      }'
  ```

### License
  - MIT License

### Acknowledgements
  - This project is inspired by Bitfumes tutorials.



