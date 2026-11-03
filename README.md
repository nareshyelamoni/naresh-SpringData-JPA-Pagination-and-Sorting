# Spring Data JPA – Pagination and Sorting

## Project Overview

This project demonstrates the implementation of **Pagination and Sorting** using Spring Data JPA in a Spring Boot application with MySQL.

Pagination helps retrieve database records in smaller groups instead of fetching all records at once. Sorting helps arrange records based on specific fields in ascending or descending order.

The main objective of this project is to understand how Spring Data JPA simplifies database operations using pagination and sorting techniques.

## Technologies Used

- **Programming Language:** Java
- **Framework:** Spring Boot
- **ORM Framework:** Hibernate
- **Persistence Framework:** Spring Data JPA
- **Database:** MySQL
- **Build Tool:** Maven
- **IDE:** Eclipse IDE
- **Version Control:** Git and GitHub

## Project Features

- Retrieve all vaccine records from the database.
- Sort records in ascending order.
- Sort records in descending order.
- Retrieve records using pagination.
- Combine pagination and sorting.
- Configure page size dynamically.
- Retrieve database records page by page.
- Use Spring Data JPA repository methods for database operations.

## Project Structure

```text
SpringDataPagingAndSorting
│
├── src/main/java
│   └── com/naresh
│       │
│       ├── SpringDataPagingAndSortingApplication.java
│       │
│       ├── model
│       │   └── Vaccine.java
│       │
│       ├── repo
│       │   ├── IvaccineRepo.java
│       │   └── PVaccineRepo.java
│       │
│       └── service
│           ├── IVaccineService.java
│           ├── PVaccineService.java
│           ├── PagingService.java
│           └── VaccineService.java
│
├── src/main/resources
│   └── application.properties
│
├── src/test/java
│
├── .gitignore
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

## Concepts Covered

### 1. Sorting

Sorting is implemented using Spring Data JPA's `Sort` class.

It allows database records to be retrieved in ascending or descending order based on a particular entity property.

**Example:**

```java
Sort sort = Sort.by(
    Direction.ASC,
    "vaccineName"
);

List<Vaccine> vaccines = repo.findAll(sort);
```

**Sorting Directions:**

- `Direction.ASC` – Retrieves records in ascending order.
- `Direction.DESC` – Retrieves records in descending order.

### 2. Pagination

Pagination is implemented using the `PageRequest` class.

It helps retrieve a limited number of records from the database for each page.

**Example:**

```java
Pageable pageable = PageRequest.of(0, 3);

Page<Vaccine> page = repo.findAll(pageable);

List<Vaccine> vaccines = page.getContent();
```

**Explanation:**

- `0` – Page number. Pagination starts from index 0.
- `3` – Number of records per page.
- `PageRequest.of()` – Creates pagination information.
- `findAll(pageable)` – Retrieves records for the requested page.
- `getContent()` – Returns the records of the requested page.

### 3. Pagination with Sorting

Spring Data JPA supports pagination and sorting together.

This allows records to be retrieved page by page in a specific sorting order.

**Example:**

```java
Sort sort = Sort.by(
    Direction.ASC,
    "vaccineName"
);

Pageable pageable = PageRequest.of(0, 3, sort);

Page<Vaccine> page = repo.findAll(pageable);

List<Vaccine> vaccines = page.getContent();
```

This retrieves three records from the first page and sorts them by vaccine name in ascending order.

### 4. Dynamic Page Size

Page size can be configured dynamically based on user requirements.

For example:

- Page size 3 – Retrieves 3 records per page.
- Page size 5 – Retrieves 5 records per page.
- Page size 10 – Retrieves 10 records per page.

This makes database record retrieval flexible.

### 5. Retrieving Records Page by Page

Using pagination, database records can be retrieved one page at a time.

The total number of records and the page size can be used to calculate the number of pages.

This approach helps manage large amounts of data efficiently.

## Database Configuration

Configure your MySQL database connection in the `application.properties` file.

**Example:**

```properties
spring.datasource.url=jdbc:mysql://localhost:3307/your_database
spring.datasource.username=your_username
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

**Configuration Details:**

- `spring.datasource.url` – MySQL database connection URL.
- `spring.datasource.username` – Database username.
- `spring.datasource.password` – Database password supplied through an environment variable.
- `spring.jpa.hibernate.ddl-auto=update` – Updates the database schema based on entity mappings.
- `spring.jpa.show-sql=true` – Displays generated SQL queries in the console.

**Note:** Replace the database name and username with your own values. Set the `DB_PASSWORD` environment variable before running the application. Never upload actual database credentials to GitHub.

## How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/nareshyelamoni/naresh-SpringData-JPA-Pagination-and-Sorting.git
```

### Step 2: Open the Project

- Open Eclipse IDE.
- Import the cloned project as an existing Maven project.
- Wait for Maven dependencies to download.

### Step 3: Configure MySQL

- Start your MySQL server.
- Create a database.
- Configure the database URL and username in `application.properties`.
- Set your database password using the `DB_PASSWORD` environment variable.

### Step 4: Run the Application

Run the main Spring Boot application class:

```java
SpringDataPagingAndSortingApplication.java
```

### Step 5: Check the Output

Execute the pagination and sorting methods and observe the retrieved records in the Eclipse console.

## Learning Outcomes

Through this project, I gained practical experience in:

- Understanding pagination and sorting in Spring Data JPA.
- Using the `Sort` class for ascending and descending order.
- Implementing pagination using `PageRequest`.
- Working with the `Pageable` and `Page` interfaces.
- Retrieving database records page by page.
- Combining pagination and sorting.
- Integrating Spring Boot with MySQL.
- Working with Hibernate and Maven.
- Managing source code using Git and GitHub.

## Future Enhancements

- Implement pagination and sorting through REST APIs.
- Add dynamic sorting based on user input.
- Implement filtering along with pagination.
- Develop a frontend interface to display paginated records.

## Author

**Naresh Yelamoni**

- GitHub: [nareshyelamoni](https://github.com/nareshyelamoni)

## Project Repository

[Spring Data JPA – Pagination and Sorting](https://github.com/nareshyelamoni/naresh-SpringData-JPA-Pagination-and-Sorting)
