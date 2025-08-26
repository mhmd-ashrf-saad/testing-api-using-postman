# API Testing Project with Postman

This project demonstrates a comprehensive approach to API testing using Postman, Newman, and a local mock server powered by JSON Server. It covers everything from basic CRUD operations to authentication workflows and automated test execution with reporting.

## Tools & Technologies

*   **[Postman](https://www.postman.com/):** API platform for building and using APIs. Used for creating and organizing API requests and test suites.
*   **[JSON Server](https://github.com/typicode/json-server):** A full fake REST API with zero coding in less than 30 seconds.
*   **[json-server-auth](https://github.com/jeremyben/json-server-auth):** A simple authentication middleware for JSON Server.
*   **[JSONPlaceholder](https://jsonplaceholder.typicode.com/):** A free fake API for testing and prototyping.
*   **[Newman](https://github.com/postmanlabs/newman):** A command-line collection runner for Postman. It allows you to run and test a Postman Collection directly from the command line.
*   **[newman-reporter-htmlextra](https://github.com/DannyDainton/newman-reporter-htmlextra):** A Newman HTML reporter that provides detailed and customizable reports.

## Project Structure

```
.
├── .gitignore
├── collection.json
├── db.json
├── locally.postman_environment.json
├── newman/
│   └── ... (HTML reports)
├── package-lock.json
├── package.json
├── server.js
└── users.json
```

## Features Practiced

*   **CRUD Operations:** Comprehensive tests for Create, Read, Update, and Delete operations.
*   **Authentication:**
    *   User registration and login endpoints.
    *   JWT (JSON Web Token) handling.
    *   Testing of secured routes that require authentication.
*   **API Request Organization:**
    *   Structuring requests in Postman collections.
    *   Using Postman environments to manage variables (e.g., base URLs, tokens).
*   **Automated Testing:**
    *   Writing tests in Postman using JavaScript.
    *   Running collections from the command line using Newman.
*   **Reporting:**
    *   Generating detailed HTML test reports.

## Running the Tests

### 1. Prerequisites

*   [Node.js](https://nodejs.org/en/) installed.
*   [Postman](https://www.postman.com/downloads/) desktop client (optional, for manual testing).

### 2. Setup

1.  Clone the repository:
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```
2.  Install the dependencies:
    ```bash
    npm install
    ```

### 3. Start the Local API Server

Run the following command to start the local JSON server with authentication middleware enabled:

```bash
npm run start-auth
```

The server will be running at `http://localhost:3000`.

### 4. Running Tests with Newman

To execute the Postman collection and generate an HTML report, run the following command in your terminal:

```bash
npx newman run collection.json -e locally.postman_environment.json -r htmlextra --reporter-htmlextra-export "newman/report.html"
```

*   `collection.json`: The Postman collection file.
*   `-e locally.postman_environment.json`: Specifies the environment file.
*   `-r htmlextra`: Enables the htmlextra reporter.
*   `--reporter-htmlextra-export "newman/report.html"`: Specifies the path to save the generated HTML report.

After the run is complete, you can find the detailed report at `newman/report.html`.

### 5. Running Tests in Postman (Manual)

1.  Open the Postman desktop client.
2.  Import the `collection.json` file.
3.  Import the `locally.postman_environment.json` file.
4.  Select the imported environment from the top-right dropdown.
5.  Run the collection using the Postman Collection Runner.

## Future Work

*   **CI/CD Integration:** Integrate the Newman tests into a Continuous Integration/Continuous Deployment (CI/CD) pipeline using **Jenkins**. This will automate the testing process on every code push or on a schedule.
