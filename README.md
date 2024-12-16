# galvez_library
# API Documentation

This is the API documentation for managing users, authors, books, and book-author relations. The API is built using the Slim framework and includes JWT-based authentication.

## Table of Contents
- [User Management](#user-management)
- [Author Management](#author-management)
- [Book Management](#book-management)
- [Book-Author Relations](#book-author-relations)
- [Setup](#setup)
- [Authorization](#authorization)

---

## User Management

### Register User
**Endpoint:** `POST /user/register`

**Description:** Register a new user.

**Payload:**
```json
{
  "username": "string",
  "password": "string"
}
```

**Response:**
```json
{
  "message": "User registered successfully."
}
```

### Authenticate User
**Endpoint:** `POST /user/authenticate`

**Description:** Authenticate user and generate an access token.

**Payload:**
```json
{
  "username": "string",
  "password": "string"
}
```

**Response:**
```json
{
  "token": "string",
  "iat": "timestamp",
  "exp": "timestamp"
}
```

---

## Author Management

### Create Author
**Endpoint:** `POST /Create`

**Description:** Create a new author.

**Payload:**
```json
{
  "name": "string",
  "bio": "string"
}
```

**Response:**
```json
{
  "message": "Author created successfully."
}
```

### Get Authors
**Endpoint:** `GET /Get`

**Description:** Retrieve all authors.

**Response:**
```json
[
  {
    "id": "integer",
    "name": "string",
    "bio": "string"
  }
]
```

### Update Author
**Endpoint:** `PUT /Update/{id}`

**Description:** Update an author by ID.

**Payload:**
```json
{
  "name": "string",
  "bio": "string"
}
```

**Response:**
```json
{
  "message": "Author updated successfully."
}
```

### Delete Author
**Endpoint:** `DELETE /Delete/{id}`

**Description:** Delete an author by ID.

**Response:**
```json
{
  "message": "Author deleted successfully."
}
```

---

## Book Management

### Create Book
**Endpoint:** `POST /Create`

**Description:** Create a new book.

**Payload:**
```json
{
  "title": "string",
  "genre": "string",
  "published_date": "string"
}
```

**Response:**
```json
{
  "message": "Book created successfully."
}
```

### Get Books
**Endpoint:** `GET /Get`

**Description:** Retrieve all books.

**Response:**
```json
[
  {
    "id": "integer",
    "title": "string",
    "genre": "string",
    "published_date": "string"
  }
]
```

### Update Book
**Endpoint:** `PUT /Update/{id}`

**Description:** Update a book by ID.

**Payload:**
```json
{
  "title": "string",
  "genre": "string",
  "published_date": "string"
}
```

**Response:**
```json
{
  "message": "Book updated successfully."
}
```

### Delete Book
**Endpoint:** `DELETE /Delete/{id}`

**Description:** Delete a book by ID.

**Response:**
```json
{
  "message": "Book deleted successfully."
}
```

### Get Books by Author ID
**Endpoint:** `GET /books/GetByAuthorId`

**Description:** Retrieve books by the author ID.

**Response:**
```json
[
  {
    "id": "integer",
    "title": "string",
    "genre": "string",
    "published_date": "string",
    "author_id": "integer"
  }
]
```

---

## Book-Author Relations

### Create Book-Author Relation
**Endpoint:** `POST /BooksAuthors`

**Description:** Create a book-author relation.

**Payload:**
```json
{
  "book_id": "integer",
  "author_id": "integer"
}
```

**Response:**
```json
{
  "message": "Relation created successfully."
}
```

### Get Book-Author Relations
**Endpoint:** `GET /BooksAuthors/Get`

**Description:** Retrieve all book-author relations.

**Response:**
```json
[
  {
    "id": "integer",
    "book_id": "integer",
    "author_id": "integer"
  }
]
```

### Delete Book-Author Relation
**Endpoint:** `DELETE /BooksAuthors/Delete/{id}`

**Description:** Delete a book-author relation by ID.

**Response:**
```json
{
  "message": "Relation deleted successfully."
}
```

---

## Setup

1. Clone the repository.
2. Install dependencies using Composer:
   ```bash
   composer install
   ```
3. Configure database connection in the PHP file.
4. Run the application:
   ```bash
   php -S localhost:8080 -t public
   ```

## Authorization

All endpoints (except user registration and authentication) require a valid JWT token in the `Authorization` header:
```
Authorization: Bearer <token>
