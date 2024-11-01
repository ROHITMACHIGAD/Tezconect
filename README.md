<!-- Detailed Setup Instructions for Job Management Application
Prerequisites
Before you start setting up the application, ensure you have the following installed:

Node.js: Download and install Node.js from nodejs.org. This includes npm (Node Package Manager) which is needed to install the application dependencies.

PostgreSQL: Download and install PostgreSQL from postgresql.org. Make sure you have access to the PostgreSQL command line (psql) or a graphical tool like pgAdmin for database management.

Code Editor: A code editor is needed to modify the application code. Visual Studio Code is recommended, but you can use any editor of your choice.

Step-by-Step Setup

Step 1: Clone the Repository
Start by cloning the project repository to your local machine. Open your terminal or command prompt and run the following command: -->

git clone <repository-url>



<!-- Step 2: Navigate to the Project Directory
After cloning, navigate into the project directory: -->

cd <project-directory>

<!-- Step 3: Install Dependencies
To install all required Node.js packages, run: -->

npm install

<!-- This command reads the package.json file and installs all listed dependencies, including Express, bcrypt, and axios.

Step 4: Set Up PostgreSQL Database
Start PostgreSQL: Ensure your PostgreSQL server is running.

Create a Database: Open your PostgreSQL command line (psql) or pgAdmin and create a new database for this application. For example: -->

CREATE DATABASE job_management;


<!-- Create Tables: Use the provided SQL queries to create the necessary tables. Execute the following commands:

Create the applicants table -->

CREATE TABLE applicants (
    id SERIAL PRIMARY KEY,
    usphno VARCHAR(15) NOT NULL,
    wkphno VARCHAR(15) NOT NULL,
    applied BOOLEAN DEFAULT TRUE,
    approved BOOLEAN DEFAULT FALSE,
    jobid INTEGER NOT NULL
);

<!-- Create the feedback table -->

CREATE TABLE feedback (
    id SERIAL PRIMARY KEY,
    feedback_text TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

<!-- Create the joblist table -->

CREATE TABLE joblist (
    id SERIAL PRIMARY KEY,
    usphno VARCHAR(15) NOT NULL,
    typeofjob VARCHAR(50) NOT NULL,
    timing VARCHAR(50) NOT NULL,
    location VARCHAR(100) NOT NULL,
    workpay NUMERIC(10, 2) NOT NULL
);

<!-- Create the users table -->
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    phno VARCHAR(15) NOT NULL,
    password VARCHAR(255) NOT NULL
);


<!-- Create the workers table -->
CREATE TABLE workers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    phno VARCHAR(15) NOT NULL,
    password VARCHAR(255) NOT NULL,
    rating INTEGER DEFAULT 0,
    jobsfinished INTEGER DEFAULT 0,
    israting BOOLEAN DEFAULT FALSE
);

<!-- Step 5: Configure the Application
API Key for OTP Verification:

Sign up at Authkey.io to get your API key for OTP services.
Find the section in your code where the API key is defined (usually in a configuration file or directly in the OTP sending function).
Replace the placeholder API key with your actual key.
Environment Variables (optional):

For sensitive information (like API keys, database credentials), consider using environment variables. You can create a .env file and use the dotenv package to load them into your application.
Step 6: Start the Application
With everything set up, you can now start your application. Run the following command in your terminal: -->

node script.js

<!-- By default, the application will run on http://localhost:3000 -->
