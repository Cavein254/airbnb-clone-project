# Airbnb Clone Project

## 📖 Overview

The **Airbnb Clone Project** is a comprehensive full-stack web application inspired by the functionality and design of the real-world Airbnb platform. The goal of this project is to simulate the process of building a scalable and secure booking platform from scratch, offering hands-on experience in software engineering best practices and modern web development workflows.

This project is ideal for learners and developers seeking to deepen their understanding of complex system architectures, backend and frontend integration, secure API development, and collaborative team development environments.

## 🎯 Project Goals

- Implement a scalable and secure backend architecture
- Design and develop REST and GraphQL APIs
- Establish relational data models and relationships
- Integrate caching with Redis for performance
- Apply best practices for API authentication and security
- Lay a foundation for a future frontend integration

## 🧰 Technology Stack

### 🔧 Backend

| Technology                | Description                                               |
| ------------------------- | --------------------------------------------------------- |
| **Django**                | High-level Python web framework used to build the backend |
| **GraphQL**               | API query language for flexible, efficient data fetching  |
| **Django REST Framework** | Toolkit for building RESTful APIs quickly and securely    |

### 🗃 Database

| Technology | Description                                                       |
| ---------- | ----------------------------------------------------------------- |
| **MySQL**  | Relational database for storing structured application data       |
| **Redis**  | In-memory key-value store used for caching and session management |

### 🧪 Testing & DevOps

- **Pytest / pytest-django** – For backend unit and integration tests.
- **Docker** – For containerized development and consistent environments.
- **Git & GitHub** – For version control and team collaboration.
- **GitHub Actions** – For continuous integration and automated testing pipelines.

## 👥 Team Roles

### 📋 Backend Developer

Responsible for designing and implementing the REST and GraphQL endpoints using Django. Duties include:

- Writing clean, maintainable backend logic
- Integrating with MySQL and Redis
- Ensuring code quality, performing code reviews, and collaborating with QA teams

### 🗃️ Database Administrator (DBA)

Manages database architecture and operations:

- Designing efficient MySQL schemas and indexing
- Handling migrations and performance tuning
- Ensuring data integrity, backup, and restore processes

### ⚙️ DevOps / SRE Engineer

Focuses on deployment, scalability, and reliability:

- Building and maintaining Docker/Docker Compose environments
- Automating CI/CD pipelines (GitHub Actions)
- Monitoring system health and enforcing best practices

### 🛡️ Quality Assurance (QA) Engineer

Ensures application quality through rigorous testing:

- Writing unit and integration tests using Pytest / pytest-django
- Automating test suites, identifying bugs, and verifying fixes
- Coordinating with backend developers to maintain high code quality

### 🧠 Product Owner / Project Manager

Guides the project’s vision, scope, and delivery:

- Defining requirements and managing the product roadmap
- Balancing timeline, quality, and scope constraints
- Facilitating communication, removing blockers, and reporting progress to stakeholders

## 💾 Database Design

Below is an overview of the core entities, essential fields, and their inter-relationships in the **Airbnb Clone Backend**:

### 👤 Users

**Key Fields:**

- `id` (PK) – Unique user identifier
- `email` (unique) – Login and contact email
- `password_hash` – Securely stored password
- `is_host` (Boolean) – Indicates if the user can list properties
- `created_at` / `updated_at` – Account timestamps  
  **Relationships:**
- A user can own multiple properties
- A user can make multiple bookings
- A user can leave multiple reviews
- A user can make multiple payments

---

### 🏠 Properties

**Key Fields:**

- `id` (PK) – Unique property ID
- `owner_id` (FK → Users) – The host of the property
- `title` – Listing title
- `description` – Detailed property details
- `price_per_night` – Nightly rate
- `location` (city, country, address) – Geographical info
  **Relationships:**
- Each property belongs to one host (user)
- A property can have multiple bookings
- A property can have multiple reviews

---

### 📅 Bookings

**Key Fields:**

- `id` (PK) – Booking ID
- `user_id` (FK → Users) – Guest who made the booking
- `property_id` (FK → Properties) – The booked property
- `start_date` / `end_date` – Booking period
- `total_price` – Calculated cost
- `status` – E.g. "pending", "confirmed", "cancelled"
  **Relationships:**
- Belongs to one user (guest)
- Belongs to one property
- Has one associated payment

---

### ⭐ Reviews

**Key Fields:**

- `id` (PK) – Review ID
- `user_id` (FK → Users) – Who wrote the review
- `property_id` (FK → Properties) – Which property is reviewed
- `rating` (int) – 1–5 star rating
- `comment` – Optional feedback
  **Relationships:**
- Written by one user
- Tied to one property

---

### 💳 Payments

**Key Fields:**

- `id` (PK) – Payment record ID
- `booking_id` (FK → Bookings) – Related booking
- `user_id` (FK → Users) – Who made the payment
- `amount` – Total charged
- `status` – E.g. "pending", "completed", "failed"
- `paid_at` / `payment_date` – Timestamp  
  **Relationships:**
- Linked to one booking
- Indirectly tied to one user via the booking

---

### 🔗 Entity Relationships (ER Summary)

| Relationship       | Type                    |
| ------------------ | ----------------------- |
| User → Property    | 1‑to‑many               |
| User → Booking     | 1‑to‑many               |
| User → Review      | 1‑to‑many               |
| User → Payment     | 1‑to‑many (via Booking) |
| Property → Booking | 1‑to‑many               |
| Property → Review  | 1‑to‑many               |
| Booking → Payment  | 1‑to‑1                  |

This relational schema ensures data consistency and creates clear connections between users, their listings, bookings, payments, and feedback.

## 🚀 Getting Started

To set up this project locally:

```bash
# Clone the repository
git clone https://github.com/cavein254/airbnb-clone-backend.git
cd airbnb-clone-backend

# Create and activate a virtual environment
python3 -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Apply migrations
python manage.py migrate

# Start the development server
python manage.py runserver
```
