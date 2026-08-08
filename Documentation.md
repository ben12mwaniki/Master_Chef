# Master Chef Documentation

## Overview

Master Chef is a recipe-sharing web application built with Flask and PostgreSQL. Users can create and share recipes, discover recipes from other users, interact through comments and likes, follow other cooks, and maintain a personal shopping list generated from recipe ingredients.

The application was developed as part of **ECSE 428 – Software Engineering Practice** at McGill University using an agile Scrum workflow.

---

## Technology Stack

- **Backend:** Flask (Python)
- **Database:** PostgreSQL
- **Frontend:** HTML, Jinja Templates, CSS, JavaScript
- **Authentication:** Session-based authentication with password hashing
- **Testing:** Pytest

---

## Core Features

### User Management
- User registration and login
- Profile management
- Edit personal information and biography
- Follow and unfollow other users

### Recipe Management
- Create, edit, and delete recipes
- Upload recipe images
- Add ingredients and preparation instructions
- Organize recipes using tags
- Search recipes by title or tag

### Community Features
- Like and unlike recipes
- Comment on recipes
- View recipes created by followed users
- View liked recipes

### Shopping List
- Add recipe ingredients to a personal shopping list
- Remove ingredients from the shopping list
- View all saved shopping items

---

## Database Design

The application uses a relational PostgreSQL database consisting of the following primary entities:

| Table | Purpose |
|--------|---------|
| Accounts | Stores user accounts and profile information |
| Recipes | Stores recipe details and authors |
| Ingredients | Stores ingredients belonging to recipes |
| Comments | Stores user comments on recipes |
| Tags | Stores recipe categories |
| Recipe_Tags | Many-to-many relationship between recipes and tags |
| Liked_Recipes | Tracks recipes liked by users |
| Followers | Tracks follower relationships between users |
| Shopping_Items | Stores ingredients saved to a user's shopping list |

The schema uses foreign key constraints and cascading deletes to maintain referential integrity.

---

## Application Structure

```
project/
├── account.py
├── recipe.py
├── recipe_query.py
├── comment.py
├── followers.py
├── likes.py
├── shopping_list.py
├── ingredient_query.py
├── tag_query.py
├── db.py
```

The application separates business logic into feature-specific modules. Route definitions are contained in `app.py`, while database operations and domain logic are encapsulated within the `project` package.

---

## Routing

The application exposes both server-rendered pages and REST-style API endpoints.

### Web Pages
- Home
- Registration/Login
- User Profiles
- Recipe Details
- Recipe Search
- Shopping List
- Account Settings

### API Endpoints
The application provides endpoints for:
- Recipe CRUD operations
- Recipe likes
- Comments
- User following
- Shopping list management
- Recipe search
- Tag retrieval

---

## Authentication

Authentication is implemented using Flask sessions. Passwords are securely stored using hashed values and verified during login using Werkzeug's password hashing utilities.

Certain actions such as creating recipes, commenting, liking recipes, and managing shopping lists require an authenticated user session.

---

## Project Architecture

The application follows a layered architecture:

```
Browser
      │
      ▼
 Flask Routes (app.py)
      │
      ▼
Business Logic (project/*.py)
      │
      ▼
PostgreSQL Database
```

This separation keeps routing, business logic, and persistence concerns independent, making the codebase easier to maintain and test.

---

## Development Process

Master Chef was developed by a team of ten students following the Scrum methodology.

Development included:
- Sprint planning
- Backlog grooming
- Feature prioritization
- Rotating team responsibilities
- Sprint retrospectives
- Collaborative code reviews through GitHub# Master Chef Technical Documentation

> For installation instructions and running the application locally, see the [README](README.md).

---

# System Overview

Master Chef is a Flask-based recipe-sharing platform backed by PostgreSQL.

The application allows users to create recipes, interact with other users, and manage cooking-related content through:

- Recipe creation and management
- User relationships
- Recipe likes and comments
- Recipe categorization
- Personal shopping lists

---

# Architecture

The application follows a layered architecture:

```
Browser
   |
   v
Flask Routes (app.py)
   |
   v
Feature Modules (project/)
   |
   v
Database Layer
   |
   v
PostgreSQL
```

## Route Layer

`app.py` defines the application's HTTP routes and handles:

- Request processing
- Session management
- Page rendering
- API requests

## Feature Modules

Application logic is separated into domain-specific modules:

```
project/
├── account.py
├── recipe.py
├── recipe_query.py
├── comment.py
├── followers.py
├── likes.py
├── shopping_list.py
├── ingredient_query.py
├── tag_query.py
└── db.py
```

Each module manages a specific application responsibility.

| Module | Responsibility |
|-|-|
| `account.py` | User account operations |
| `recipe.py` | Recipe creation and modification |
| `recipe_query.py` | Recipe retrieval and searching |
| `comment.py` | Recipe comments |
| `likes.py` | Recipe likes |
| `followers.py` | User relationships |
| `shopping_list.py` | Shopping list operations |

---

# Database Design

Master Chef uses a relational PostgreSQL database.

## Main Entities

| Entity | Purpose |
|-|-|
| Accounts | Stores user profiles and authentication information |
| Recipes | Stores recipe content and ownership |
| Ingredients | Stores recipe ingredients |
| Comments | Stores recipe discussions |
| Tags | Stores recipe categories |
| Recipe_Tags | Links recipes and tags |
| Liked_Recipes | Tracks user likes |
| Followers | Tracks user relationships |
| Shopping_Items | Stores personal shopping lists |

---

# Data Relationships

Important relationships include:

### Users and Recipes

One user can create multiple recipes.

```
Account 1 ---- * Recipe
```

### Recipes and Tags

Recipes can have multiple tags, and tags can belong to multiple recipes.

```
Recipe * ---- * Tag
```

### Users and Likes

Users can like multiple recipes.

```
Account * ---- * Recipe
```

### Followers

Users can follow other users through a self-referencing relationship.

```
Account * ---- * Account
```

---

# API Design

The backend provides API endpoints for dynamic operations.

| Category | Functionality |
|-|-|
| Recipes | Create, edit, delete, search |
| Users | Account lookup and profiles |
| Social | Likes, comments, following |
| Shopping | Add/remove ingredients |
| Tags | Recipe categorization |

---

# Security

## Authentication

Authentication uses Flask sessions.

User passwords are protected using Werkzeug password hashing.

Passwords are never stored directly.

## Authorization

Actions requiring ownership or authentication include:

- Creating recipes
- Editing recipes
- Deleting recipes
- Commenting
- Managing shopping lists

---

# Testing Strategy

Automated tests are implemented using Pytest.

Testing focuses on:

- Account functionality
- Recipe operations
- API behavior
- User interactions

---

# Development Process

The team followed Scrum methodology.

Practices included:

- Sprint planning
- Backlog grooming
- Feature prioritization
- Rotating responsibilities
- Sprint retrospectives
- Collaborative GitHub workflows

---

# Future Improvements

Potential enhancements:

- Recipe recommendation system
- Advanced search
- Personalized feeds
- Notifications
- Mobile application support