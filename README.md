# E-commerce Catalog Service

## Overview

The **E-commerce Catalog Service** manages the product catalog for the e-commerce platform. It handles all product-related operations, including adding, updating, removing, and searching for products. This service interacts with other services like the API Gateway and integrates with the **E-commerce User Service** for managing product reviews and user-specific preferences.

## Features

- **Product Management**: Add, update, and remove products from the catalog.
- **Product Search**: Allows users to search for products by various filters (e.g., category, price, availability).
- **Category Management**: Organize products into categories and subcategories.
- **Inter-Service Communication**: Connects with the **E-commerce API Gateway**, **E-commerce Cart Service**, and **E-commerce Order Service** to share product details.

## Technologies Used

- **Java**
- **Spring Boot**
- **Maven** (for dependency management)
- **PostgreSQL** (for product data storage)
- **Elasticsearch** (optional, for enhanced product search functionality)

## Prerequisites

Before running this service, ensure you have the following:

- **Java JDK 11 or higher**
- **Maven** (for building the project)
- A running **PostgreSQL** database (or other supported database).
- Access to the relevant microservices (e.g., API Gateway, Cart Service).

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/juansebstt/ecommerce-catalog-service.git
    ```

2. Navigate to the project directory:

    ```bash
    cd ecommerce-catalog-service
    ```

3. Build the project using Maven:

    ```bash
    mvn clean install
    ```


## Configuration

You need to configure the database and application settings in your `application.yml` or `application.properties` file.

### Sample Configuration

```yaml
server:
  port: 8083

spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/ecommerce_catalog_db
    username: yourUsername
    password: yourPassword
    driver-class-name: org.postgresql.Driver

  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

  application:
    name: ecommerce-catalog-service
```

## Inter-Service Communication

The **E-commerce Catalog Service** communicates with the following microservices:

- **[E-commerce API Gateway](https://github.com/juansebstt/ecommerce-api-gateway)**:
    - Routes product-related requests (e.g., searching for products, retrieving product details) to the Catalog Service.
- **[E-commerce Cart Service](https://github.com/juansebstt/ecommerce-cart-service)**:
    - Fetches product details to add items to a user's shopping cart.
- **[E-commerce Order Service](https://github.com/juansebstt/ecommerce-order-service)**:
    - Retrieves product information when creating an order.
- **[E-commerce User Service](https://github.com/juansebstt/ecommerce-user-service)**:
    - Manages user reviews and ratings for products.

## Usage

### Adding a Product

To add a product to the catalog, make a POST request to the `/products` endpoint with the following payload:

```json
{
  "name": "New Product",
  "description": "A great new product",
  "price": 19.99,
  "category": "Electronics",
  "stock": 100
}

```

### Searching for Products

Users can search for products using various filters such as category, price range, or keywords. Use a GET request to `/products/search` with the desired parameters.

## Testing

You can use tools like **Postman** or **curl** to test the various API endpoints. Ensure proper authentication is in place if the service is secured.

## Contributing

Feel free to submit pull requests or open issues if you find bugs or want to contribute to the project.