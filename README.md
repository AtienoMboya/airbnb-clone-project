# Airbnb Clone Project
A full-stack web application that simulates a real-world booking platform like Airbnb. This project focuses on backend systems, database design, RESTful APIs, and security, offering hands-on experience with scalable architecture and collaborative development workflows.

## 🚀 Project Goals

- **Understand Full-Stack Architecture**  
  Gain practical experience building both frontend and backend components of a scalable web application.

- **Implement Backend Systems**  
  Design and develop core backend features such as user authentication, data persistence, and session management.

- **Design and Integrate Databases**  
  Model real-world entities (users, places, bookings) using relational databases and apply ORM principles.

- **Develop RESTful APIs**  
  Create robust, well-documented APIs to handle user interaction, CRUD operations, and system integrations.

- **Apply Application Security Best Practices**  
  Implement secure user authentication, input validation, and permission handling to protect sensitive data.

- **Practice Scalable Design Patterns**  
  Use modular, maintainable code structures that support scalability and future feature growth.

- **Foster Team Collaboration**  
  Collaborate in a team setting using version control (Git), issue tracking, code reviews, and clear communication.

- **Simulate Real-World Workflow**  
  Follow industry-standard development practices, including Agile methodology, continuous integration, and testing.

## 👥 Team Roles

### Core Roles
- **Backend Developer**  
  Implements business logic, API endpoints, authentication, and server-side workflows.

- **Database Administrator (DBA)**  
  Designs and optimizes PostgreSQL schemas, indexes, migrations, query performance, and backups.

- **DevOps Engineer**  
  Builds and maintains CI/CD pipelines, Docker environments, deployment scripts, monitoring, and cloud infrastructure.

- **QA Engineer**  
  Designs and executes manual and automated tests to ensure quality, reliability, and performance across the application.

### Additional Recommended Roles
 *([Inspired by common software team structures for scalable projects](https://itrexgroup.com/blog/software-development-team-structure/))*

- **Product Owner**  
  Defines project vision, prioritizes backlog, and ensures the end product aligns with business goals.

- **Project Manager / Scrum Master**  
  Coordinates tasks, manages timelines, removes blockers, and maintains Agile workflows.

- **Software Architect / Tech Lead**  
  Oversees system architecture, enforces coding standards, and guides technical design decisions.

- **Frontend Developer** *(if applicable)*  
  Implements user interfaces and interacts with APIs to deliver smooth user experiences.

- **UX/UI Designer**  
  Crafts wireframes, prototypes, and ensures a user-centered design and intuitive interface.

- **Business Analyst**  
  Bridges business needs and technical requirements; refines user stories and functional specifications.

- **Test Automation Engineer**  
  Builds and maintains automated test suites, integrating them into CI/CD to ensure fast, reliable feedback.



## 🛠️ Technology Stack

This project leverages a modern full-stack setup with the following technologies:

- **[Django](https://www.djangoproject.com/)** – High-level Python web framework for rapid development.
- **[Django REST Framework](https://www.django-rest-framework.org/)** – Powerful toolkit for building Web APIs.
- **[PostgreSQL](https://www.postgresql.org/)** – Robust, open-source relational database system.
- **[GraphQL](https://graphql.org/)** – Flexible query language for APIs and runtime for fulfilling those queries.
- **[Celery](https://docs.celeryq.dev/)** – Distributed task queue for asynchronous job processing.
- **[Redis](https://redis.io/)** – In-memory data store used as a message broker for Celery and caching.
- **[Docker](https://www.docker.com/)** – Containerization for consistent development and deployment environments.
- **CI/CD Pipelines** – Automates testing and deployment workflows (e.g., GitHub Actions).

## 🗃️ Database Design

The project is structured around five core entities that reflect real-world components of a booking platform like Airbnb. Below is an overview of each entity, its key fields, and how the entities relate to one another.

### 🔹 Users
Represents platform users (both hosts and guests).

**Key Fields:**
- `id` – Unique identifier
- `name` – Full name of the user
- `email` – Unique email for authentication
- `role` – Indicates whether the user is a host, guest, or both
- `created_at` – Timestamp of account creation

### 🔹 Properties
Represents listings posted by hosts.

**Key Fields:**
- `id` – Unique identifier
- `user_id` – Foreign key to the host (User)
- `title` – Name of the listing
- `description` – Detailed property info
- `location` – City, region, or coordinates

**Relationships:**
- A **User** (host) can have **many Properties**
- A **Property** belongs to one **User**

### 🔹 Bookings
Captures reservations made by guests.

**Key Fields:**
- `id` – Unique identifier
- `user_id` – Guest who made the booking
- `property_id` – The booked property
- `start_date` – Booking start date
- `end_date` – Booking end date

**Relationships:**
- A **User** (guest) can have **many Bookings**
- A **Booking** belongs to one **Property**
- A **Booking** is made by one **User**

### 🔹 Payments
Tracks transactions related to bookings.

**Key Fields:**
- `id` – Unique identifier
- `booking_id` – Related booking
- `amount` – Total paid
- `status` – Payment status (e.g., pending, completed, failed)
- `timestamp` – Time of payment

**Relationships:**
- A **Payment** is linked to one **Booking**
- A **Booking** can have one **Payment**

### 🔹 Reviews
Captures feedback from guests after a stay.

**Key Fields:**
- `id` – Unique identifier
- `user_id` – Guest who left the review
- `property_id` – The reviewed property
- `rating` – Numerical rating
- `comment` – Optional text feedback

**Relationships:**
- A **User** can write **many Reviews**
- A **Property** can have **many Reviews**
- A **Review** belongs to both a **User** and a **Property**

---

**Entity Relationship Summary:**

- One **User** can own many **Properties** (if host)
- One **User** can make many **Bookings** (if guest)
- One **Property** can have many **Bookings** and **Reviews**
- One **Booking** is associated with one **Payment**
- One **User** can write many **Reviews**

