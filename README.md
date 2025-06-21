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

## 🧰 Tech Stack

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
