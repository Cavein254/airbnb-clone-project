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

## 🧩 Feature Breakdown

The Airbnb Clone Backend is designed around modular, scalable features that mirror the core functionality of a real-world booking platform. Below is a summary of the major features and how they contribute to the overall system:

### 👤 User Management

Handles user registration, login, authentication (JWT), and role-based access (host or guest). This ensures secure access control and sets the foundation for user-specific content like property listings and bookings.

### 🏠 Property Management

Allows hosts to create, update, and manage property listings. Includes support for pricing, availability, and descriptions — forming the core content of the platform that guests browse and book.

### 📅 Booking System

Enables guests to book available properties by selecting check-in/check-out dates and confirming reservations. It enforces availability constraints and calculates total cost, ensuring booking accuracy and preventing conflicts.

### 💳 Payment Integration

Manages payment tracking for bookings, including status updates (pending, completed, failed). Although third-party gateways are not integrated in this backend-only phase, the structure supports future integration with providers like Stripe or PayPal.

### ⭐ Review System

Guests can leave reviews and ratings for properties they’ve stayed in. This feature enhances user trust and transparency by offering peer-to-peer feedback that influences future booking decisions.

### 🧾 Admin & Reporting (Planned)

An admin panel will support moderation, analytics, and data management. This includes user verification, listing approval workflows, and system health insights to aid in platform governance and operational oversight.

## 🔐 API Security

Ensuring robust API security is critical for protecting sensitive user data, preventing abuse, and maintaining trust across the platform. Below are the key security measures implemented in the Airbnb Clone Backend:

### 🔑 Authentication

We use **JWT (JSON Web Tokens)** for stateless user authentication. Access tokens are short-lived and securely transmitted in headers, while refresh tokens are used to renew sessions without forcing repeated logins. This prevents unauthorized access and keeps session management scalable.

> 🔒 **Why it matters**: Prevents account hijacking, ensures only verified users can access protected routes like booking or property creation.

---

### 🛂 Authorization

Role-based access control (RBAC) ensures users can only perform actions appropriate to their role (e.g., host vs guest). For example, only hosts can list properties, and only the user who made a booking can cancel it.

> 🔒 **Why it matters**: Enforces user boundaries, prevents privilege escalation, and safeguards user-owned resources.

---

### 🚦 Rate Limiting

Rate limiting and request throttling will be enforced (e.g., via **Redis + Django Ratelimit**) to mitigate abuse, brute-force attacks, and DDoS attempts on login or search endpoints.

> 🔒 **Why it matters**: Protects the platform from spamming, excessive load, and malicious automation.

---

### 🧼 Input Validation & Sanitization

All inputs (especially from public-facing endpoints like reviews or listings) are validated and sanitized using Django and DRF serializers to prevent SQL injection, XSS, and malformed data.

> 🔒 **Why it matters**: Shields the database and users from malicious or malformed input that could compromise system integrity.

---

### 🧾 Secure Payment Handling (Planned)

While payment processing integration is out of scope for the backend-only phase, the architecture ensures sensitive payment actions (like initiating or confirming payments) are restricted and audit-logged.

> 🔒 **Why it matters**: Lays the groundwork for safe integration with third-party processors (e.g., Stripe), reducing the risk of financial fraud or transaction tampering.

---

### 🧯 Error Handling & Logging

Error messages are generalized for users but logged with full context for admins. Sensitive information is never exposed in responses.

> 🔒 **Why it matters**: Prevents attackers from gaining internal insights and supports incident response and debugging.

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
