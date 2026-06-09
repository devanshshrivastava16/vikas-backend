# Vikas - Omnichannel Marketplace

An omnichannel marketplace backend API designed to provide a better customer shopping experience. Built with Spring Boot, this e-commerce platform provides a comprehensive set of features ranging from secure user authentication to order management.

## 🚀 Features

*   **Authentication & Authorization:** Secure JWT-based authentication with Role-Based Access Control (RBAC).
*   **User Roles:** Support for `ADMIN`, `SELLER`, and `USER` roles.
*   **Product Management:** Add, update, delete, and view products and categories.
*   **Cart Management:** Users can add products to their cart, update quantities, and remove items.
*   **Order Processing:** Checkout cart, place orders, and track order items with simulated payment processing.
*   **Address Management:** Users can add and manage shipping addresses.
*   **Image/File Upload:** Support for uploading product images.

## 🛠️ Tech Stack

*   **Java 21**
*   **Spring Boot** (Web, Data JPA, Security, Validation)
*   **Database:** H2 Database (in-memory for development/testing), easily switchable to PostgreSQL via `application.properties`.
*   **Security:** Spring Security + JSON Web Tokens (JWT)
*   **Build Tool:** Maven
*   **Utilities:** Lombok, ModelMapper
*   **Containerization:** Docker

## 🚦 Getting Started

### Prerequisites
*   Java 21 installed
*   Maven installed (or you can use the included Maven wrapper)
*   Docker (Optional, for containerized execution)

### Running Locally

1.  **Navigate to the project directory:**
    ```bash
    cd vikas
    ```
2.  **Run the application using the Maven wrapper:**
    ```bash
    # On Windows:
    mvnw.cmd spring-boot:run
    
    # On Linux/Mac:
    ./mvnw spring-boot:run
    ```

The application will start on `http://localhost:8080`. 
The H2 Database console is enabled by default and can be accessed at `http://localhost:8080/h2-console` using the JDBC URL `jdbc:h2:mem:test`.

### Running with Docker

You can build and run the application using Docker:

1.  **Build the Docker image:**
    ```bash
    docker build -t vikas-backend .
    ```
2.  **Run the container:**
    ```bash
    docker run -p 8080:8080 vikas-backend
    ```

## 🔐 Default Test Accounts

The application automatically seeds the database with the following test accounts on startup to help with testing:

| Role   | Username  | Password    |
|--------|-----------|-------------|
| ADMIN  | admin     | adminPass   |
| SELLER | seller1   | password2   |
| USER   | user1     | password1   |

## 🛡️ Security Endpoints Overview
*   `/api/auth/**`: Public endpoints for Login and Registration.
*   `/api/public/**`: Publicly accessible data (e.g., viewing products/categories).
*   `/api/admin/**`: Requires `ROLE_ADMIN`.
*   `/api/seller/**`: Requires `ROLE_SELLER` or `ROLE_ADMIN`.
*   `/swagger-ui/**`, `/v3/api-docs/**`: Publicly available API documentation.