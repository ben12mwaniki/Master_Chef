# Master Chef 🍳

A social recipe-sharing platform built with Flask and PostgreSQL.

Master Chef allows users to discover, create, and interact with recipes. Users can share their own recipes, organize them using tags, follow other cooks, comment on recipes, like recipes, and manage ingredients through a personalized shopping list.

This project was originally developed as part of **ECSE 428 - Software Engineering Practice** at McGill University during Fall 2022. The team followed Scrum practices throughout development, including sprint planning, backlog grooming, feature prioritization, and retrospectives.

---

# Live Demo

The deployed application is available here:

🔗 [Master Chef Application](https://master-chef-3bhn.onrender.com/)

---

# Screenshots

## Recipe Discovery

![Recipe Search](PLACEHOLDER_IMAGE_URL)

## Recipe Details

![Recipe Page](PLACEHOLDER_IMAGE_URL)

## Shopping List

![Shopping List](PLACEHOLDER_IMAGE_URL)

---

# Features

## 🍲 Recipe Sharing

Users can:

- Create, edit, and delete recipes
- Add ingredients and cooking instructions
- Upload recipe images
- Organize recipes using tags
- Search for recipes

## 👥 Social Interaction

Users can:

- Follow other users
- Like and unlike recipes
- Comment on recipes
- View recipes from followed users
- Browse liked recipes

## 🛒 Shopping List

Users can:

- Add recipe ingredients to a personal shopping list
- Remove shopping items
- Track ingredients needed for cooking
- Print shopping list

## 🔐 User Accounts

Users can:

- Register and authenticate accounts
- Manage their profiles
- Update personal information

---

# Technology Stack

| Layer | Technology |
|---|---|
| Backend | Flask (Python) |
| Database | PostgreSQL |
| Frontend | HTML, CSS, JavaScript, Jinja Templates |
| Authentication | Flask Sessions + Werkzeug Password Hashing |
| Testing | Pytest |
| Deployment | PLACEHOLDER |

---

# Application Overview

Master Chef follows a layered backend architecture:

```
Browser
   |
   v
Flask Routes
   |
   v
Feature Modules
   |
   v
PostgreSQL Database
```

The application separates request handling, business logic, and database operations to keep the codebase modular and maintainable.

For detailed architecture information:

➡️ [View Technical Documentation](DOCUMENTATION.md)

---

# Running Locally

## Prerequisites

- Python 3
- PostgreSQL 16

## Setup

Clone the repository:

```bash
git clone https://github.com/ben12mwaniki/Master_Chef.git
cd MasterChef
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate the environment:

Linux/macOS:

```bash
source .venv/bin/activate
```

Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt && pip install -r requirements-dev.txt
```

---

## Configuration

Create a `.env` file:

```env
DEBUG=false

SECRET_KEY=your_secret_key

POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_password
POSTGRES_DB=masterchef
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
```

---

## Running the Application

Start the Flask server:

```bash
flask run
```

The application will be available at:

```
http://127.0.0.1:5000
```

---

# Testing

Run automated tests:

```bash
pytest --cov=project --cov-branch --cov-report term
```

---

# Contributors

- Ruoli Wang
- Sia Ham
- Tyler Syme
- Zheyan Tu
- Sandy Lao
- Theodore Peters
- Paul Teng
- Niilo Vuokila
- Jasmine Cheung
- Ben Mwaniki
