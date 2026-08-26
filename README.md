# Local Library - Admin Dashboard

A comprehensive dashboard application for local library management. This project provides analytical metrics and statistics regarding library accounts, cataloged books, authors, borrowing records, and popular trends to help library administrators manage their resources effectively.

---

## 📌 Project Overview

**Local Library** is designed to process and analyze dataset arrays containing information about accounts, authors, and books. The dashboard consists of three main views:

1. **Overall Stats (Home View)**: Displays high-level library metrics, including total cataloged books, currently borrowed books, registered accounts, top 5 most common genres, top 5 most popular books, and top 5 most popular authors.
2. **Stats by Book (Books View)**: Allows administrators to search, filter, and partition books based on borrowing status (currently checked out vs. returned), as well as inspect borrower history for specific books.
3. **Stats by Account (Accounts View)**: Provides tools for searching accounts, sorting user records alphabetically, inspecting borrow counts, and listing all books currently in possession of a specific account.

---

## 🚀 Technology Stack

- **Frontend**: JavaScript (ES6+), HTML5, Bootstrap 4, Vanilla CSS
- **Backend / Tooling**: Node.js, `live-server`
- **Testing Framework**: Mocha & Chai
- **Containerization (Optional)**: Docker

---

## 🛠️ Project Structure

```text
project-local-library/
├── docs/
│   └── function-instructions.md    # Detailed specifications for helper functions
├── public/
│   ├── index.html                  # Home / Dashboard overview page
│   ├── books.html                  # Books statistics page
│   ├── accounts.html               # Accounts management page
│   ├── setup.js                    # Environment setup script
│   ├── data/                       # Sample dataset files (accounts, authors, books)
│   ├── renderers/                  # DOM rendering scripts for pages
│   └── src/                        # Core JavaScript business logic modules
│       ├── accounts.js             # Account helper functions
│       ├── books.js                # Book helper functions
│       └── home.js                 # Dashboard summary & analytics helper functions
├── test/                           # Automated test suites
│   ├── accounts.test.js
│   ├── books.test.js
│   └── main.test.js
├── package.json                    # Dependencies and npm scripts
└── README.md                       # Project documentation
```

---

## ⚡ Core Functions & API Reference

### 1. Accounts Module (`public/src/accounts.js`)

- `findAccountById(accounts, id)`: Returns the account object matching the given string ID.
- `sortAccountsByLastName(accounts)`: Returns an array of account objects sorted alphabetically by last name.
- `getTotalNumberOfBorrows(account, books)`: Returns the total number of times an account's ID appears in any book's borrow records.
- `getBooksPossessedByAccount(account, books, authors)`: Returns an array of book objects currently checked out by the account, with nested author information inside each book object.

### 2. Books Module (`public/src/books.js`)

- `findAuthorById(authors, id)`: Returns the author object matching the specified integer ID.
- `findBookById(books, id)`: Returns the book object matching the specified string ID.
- `partitionBooksByBorrowedStatus(books)`: Returns an array containing two nested arrays:
  1. Books currently checked out (`returned === false`).
  2. Books that have been returned (`returned === true`).
- `getBorrowersForBook(book, accounts)`: Returns an array of up to 10 account objects that borrowed the specified book, enriched with their borrowing return status.

### 3. Home / Analytics Module (`public/src/home.js`)

- `getTotalBooksCount(books)`: Returns total count of books in the library.
- `getTotalAccountsCount(accounts)`: Returns total count of registered library accounts.
- `getBooksBorrowedCount(books)`: Returns total count of books currently checked out.
- `getMostCommonGenres(books)`: Returns an array of up to 5 objects representing the most common genres in descending order (`{ name: string, count: number }`).
- `getMostPopularBooks(books)`: Returns an array of up to 5 objects representing the most borrowed books in descending order (`{ name: string, count: number }`).
- `getMostPopularAuthors(books, authors)`: Returns an array of up to 5 objects representing the most popular authors based on total borrows across all their written books (`{ name: string, count: number }`).

---

## 💻 Getting Started

### Prerequisites

Ensure you have the following installed on your machine:
- [Node.js](https://nodejs.org/) (v14.0 or higher recommended)
- [npm](https://www.npmjs.com/) (included with Node.js)

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd project-local-library
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

---

## 🏃 Running the Application

To launch the local development server:

```bash
npm start
```

This starts `live-server` and serves the application at `http://127.0.0.1:8080` (or `http://localhost:8080`), automatically opening your default web browser.

---

## 🧪 Running Tests

To execute the Mocha unit test suite and verify function implementations:

```bash
npm test
```

All 20 unit tests across account, book, and home modules should run and pass cleanly.

---

## 🐳 Running with Docker (Optional)

If Docker is installed on your system, you can build and run the containerized application:

- **Build Docker Image**:
  ```bash
  npm run docker:build
  ```

- **Run Docker Container**:
  ```bash
  npm run docker:run
  ```

- **Run Tests in Docker**:
  ```bash
  npm run docker:test
  ```

- **Stop Docker Containers**:
  ```bash
  npm run docker:stop
  ```

---

## 📄 License

This project is licensed under the ISC License.
