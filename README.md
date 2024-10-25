Rule Engine Application
This project is a simple 3-tier rule engine application that allows users to define, combine, and evaluate conditional rules for eligibility determination using an Abstract Syntax Tree (AST) structure. The project includes a user interface (UI) for rule input, an API for rule management, and a backend for data storage.

Table of Contents
Project Overview
Features
Design Choices
Requirements
Setup and Installation
Running the Application
Docker Containerization
Testing
Project Overview
This rule engine application uses a 3-tier architecture, implemented as:

UI Layer: Allows users to input, view, and manage rules.
API Layer: Manages rule creation, combination, and evaluation.
Backend: Stores rules and application data in a lightweight SQLite database.


Features
Abstract Syntax Tree (AST): Transforms rules into an AST structure, making rule creation and evaluation flexible and efficient.
Dynamic Rule Changes: Supports rule creation, modification, and combination.
Node Structure: Represents rules as "operator" or "operand" nodes.
Database: Stores rule data and metadata, supporting SQLite for simplicity and easy deployment.
Design Choices
AST Representation: Chosen to manage complex logical expressions, enabling rule evaluation to be dynamically handled at runtime.
SQLite for Data Storage: Selected for simplicity, portability, and ease of use in small-scale applications.
Class-Based Structure: The Node class encapsulates each component of the rule, allowing easier extension and testing of rule functionality.


Requirements
Python 3.8+
Libraries: sqlite3, ast, unittest


Dependencies
To run and test this application, ensure the following Python packages and dependencies are available:   

pip install ast sqlite3 json unittest

Docker and Podman Containers
This application can be containerized to simplify the deployment process.

Required Containers
Python Runtime: Use a lightweight Python container for running the application.
SQLite Database: The application uses SQLite, which is included in most Python runtime images.

# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any necessary dependencies
RUN pip install -r requirements.txt

# Command to run the app
CMD ["python", "rule_engine.py"]

Build and Run with Docker
# Build the Docker image
docker build -t rule-engine .

# Run the Docker container
docker run -d -p 5000:5000 rule-engine

Setup and Installation

Clone the repository:
git clone <repo-url>
cd rule-engine

Create and Initialize Database: Run the following Python script to set up the SQLite database and tables.
python database_setup.py

Run Application: Run the application with:
python rule_engine.py

Running the Application
The application can be run locally by following the steps in Setup and Installation.

Alternatively, using the provided Docker setup, the application can be run within a container to simplify the deployment process.

Testing
The project includes a set of unit tests to validate rule creation, combination, and evaluation.

Running Tests
To run tests:

python -m unittest test_rule_engine.py

















