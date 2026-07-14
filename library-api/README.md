# 📚 Library API

**Student Admission Number:** C027-01-0839/2024

A RESTful Library Management API built using **FastAPI**, **SQLModel**, and **PostgreSQL**. The API allows users to manage books and categories through CRUD operations and provides search and filtering capabilities.

---

## Features

* Create book categories
* Add new books
* List all books
* Filter books by availability
* Search books by author or title
* Retrieve a single book by ID
* Update existing book details
* Automatic API documentation with Swagger UI

---

## Technologies Used

* Python 3.11+
* FastAPI
* SQLModel
* PostgreSQL
* SQLAlchemy
* Uvicorn

---

## Project Structure

```text
library-api/
│
├── database/
│   └── session.py
│
├── models/
│   ├── book.py
│   └── category.py
│
├── main.py
├── requirements.txt
├── docker-compose.yml
├── Dockerfile
└── README.md
```

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/library-api.git
cd library-api
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it:

**Windows**

```bash
venv\Scripts\activate
```

**Linux/macOS**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Database

Start PostgreSQL using Docker Compose.

```bash
docker compose up -d
```

Example configuration:

* Database: `library_db`
* Username: `postgres`
* Password: `postgres`
* Port: `5432`

The application automatically creates the database tables on startup.

---

## Running the Application

Start the FastAPI server with:

```bash
uvicorn main:app --reload
```

The API will be available at:

```
http://127.0.0.1:8000
```

---

## API Documentation

Swagger UI

```
http://127.0.0.1:8000/docs
```

ReDoc

```
http://127.0.0.1:8000/redoc
```

---

## API Endpoints

### Root

| Method | Endpoint | Description     |
| ------ | -------- | --------------- |
| GET    | `/`      | Welcome message |

---

### Categories

| Method | Endpoint      | Description           |
| ------ | ------------- | --------------------- |
| POST   | `/categories` | Create a new category |

Example Request

```
POST /categories?name=Science Fiction
```

---

### Books

#### Create Book

| Method | Endpoint |
| ------ | -------- |
| POST   | `/books` |

Example JSON

```json
{
  "title": "Clean Code",
  "author": "Robert C. Martin",
  "available": true,
  "category_id": 1
}
```

---

#### List Books

| Method | Endpoint |
| ------ | -------- |
| GET    | `/books` |

Optional Query Parameters

| Parameter | Description               |
| --------- | ------------------------- |
| skip      | Number of records to skip |
| limit     | Maximum records returned  |
| available | Filter available books    |

Example

```
GET /books?available=true&skip=0&limit=10
```

---

#### Search Books

| Method | Endpoint        |
| ------ | --------------- |
| GET    | `/books/search` |

Query Parameters

| Parameter | Description              |
| --------- | ------------------------ |
| author    | Search by author         |
| title     | Search by title          |
| q         | General search parameter |

Example

```
GET /books/search?author=Martin
```

---

#### Get Book by ID

| Method | Endpoint           |
| ------ | ------------------ |
| GET    | `/books/{book_id}` |

Example

```
GET /books/1
```

---

#### Update Book

| Method | Endpoint           |
| ------ | ------------------ |
| PATCH  | `/books/{book_id}` |

Example JSON

```json
{
  "title": "Clean Code (Second Edition)",
  "available": false
}
```

---

## Example Response

```json
{
  "id": 1,
  "title": "Clean Code",
  "author": "james orengo",
  "available": true,
  "category_id": 1,
  "created_at": "2026-07-10T10:00:00",
  "updated_at": "2026-07-10T10:00:00"
}
```

---

## Error Responses

### Book Not Found

```json
{
  "detail": "Book not found"
}
```

Status Code:

```
404 Not Found
```

---

## Author

**Student:** C027-01-0839/2024

Dedan Kimathi University of Technology

Bachelor of Science in Business Information Technology (BBIT)

---

## Version

**Current Version:** 1.0.0

---

## License

This project is developed for educational purposes as part of a university laboratory assignment.
