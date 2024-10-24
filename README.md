# Choco House Application

## Problem Statement
Create a Simple Python Application for a fictional chocolate house that uses SQLite to manage,
Seasonal flavor offerings 
Ingredient inventory
Customer flavor suggestions and allergy concerns


## Overview
This is a Django-based web application for a fictional chocolate house. It allows management of:
- *Seasonal flavor offerings*: Displays current flavors available for a season.
- *Ingredient inventory*: Tracks the stock of ingredients used for flavors.
- *Customer flavor suggestions and allergy concerns*: Customers can suggest flavors and report allergy concerns.

This application uses *SQLite* as the database and includes *Docker* for easy setup.

## Prerequisites
Before you begin, ensure you have the following installed on your machine:
- Python 3.9+
- Docker and Docker Compose

## Installation

### Step 1: Clone the repository
Clone the project to your local machine:
 Unzip the repository

git clone https://github.com/yourusername/choco-house.git
cd choco-house

### Step 2: Create and activate a virtual environment

It’s a good practice to use a virtual environment for Python projects:

python -m venv env
source env/bin/activate  # On Windows use env\Scripts\activate

### Step 3: Install dependencies

Install the required packages from requirements.txt:

pip install -r requirements.txt

### Step 4: Set up the database

Run the following commands to apply the migrations and set up the SQLite database:

python manage.py migrate

### Step 5: Create a superuser (optional)

If you want to access the admin interface:

python manage.py createsuperuser

### Step 6: Run the development server

Start the Django development server:

python manage.py runserver

The app will be available at http://127.0.0.1:8000/.

## Using Docker

### Step 1: Build and run the Docker container

Make sure Docker is installed and running on your system. Then, build and start the container using docker-compose:

docker-compose up --build

This will run the app inside a Docker container, exposing it at http://localhost:8000/.

### Step 2: Stopping the containers

To stop the running Docker containers:

docker-compose down

Application Features

1. Seasonal Flavors

The application displays the current seasonal flavors that are available. Navigate to:

http://127.0.0.1:8000/flavors/

2. Customer Flavor Suggestions

Customers can submit flavor suggestions and report allergy concerns at:

http://127.0.0.1:8000/suggestions/

3. Admin Interface

If you created a superuser, you can log in to the Django admin interface to manage seasonal flavors, ingredients, and customer suggestions:

http://127.0.0.1:8000/admin/

Running Tests

To validate the application functionality, use the following command to run the test cases:

python manage.py test

The tests include:

Checking if the seasonal flavors are displayed correctly.

Validating customer suggestions form.


Edge Case Handling

Here are some edge cases considered in the project:

1. No Seasonal Flavors Available: If no seasonal flavors are available, a message is shown to the user.


2. Empty Customer Suggestions: When a user submits the form without filling in required fields, appropriate validation messages are shown.


3. Allergy Concern Field: If a customer doesn’t have any allergy concerns, the field can be left blank.



SQL Queries and ORM Abstraction

The application primarily uses Django's ORM to interact with the SQLite database. For example:

# Get all seasonal flavors that are still available
flavors = SeasonalFlavor.objects.filter(available_until__gte=datetime.date.today())

No direct SQL queries were used, adhering to Django's ORM abstraction.

Docker Build and Run Commands

1. Build Docker Containers


2. Run the Application: The app will run at http://localhost:8000/.


3. Stop Docker Containers:

docker-compose down



## Project Structure

choco_house/
│
├── choco_house/               # Project-level settings
│   ├── settings.py            # Django settings
│   ├── urls.py                # Project URL routing
│   └── ...
│
├── inventory/                 # App to manage flavors, ingredients, suggestions
│   ├── models.py              # Models for the database
│   ├── views.py               # Application views (logic)
│   ├── templates/             # HTML templates for the views
│   ├── tests.py               # Unit tests for the application
│   └── ...
│
├── db.sqlite3                 # SQLite Database file
├── Dockerfile                 # Dockerfile to containerize the app
├── docker-compose.yml          # Docker Compose for multi-container setup
├── requirements.txt           # List of dependencies
└── README.md                  # This file


Additional Notes

Ensure Docker is running if you choose the containerized version.

Handle form validations on the front-end and back-end for user inputs.

