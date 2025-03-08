# API Testing Project (With Basic Requests)

## Project Overview

This project is an API testing suite created to validate the basic functionality of various endpoints. The tests are created using **Postman** and executed using **Newman**. The objective of the project is to ensure that the APIs are functioning as expected, handling some basic edge cases, and returning the correct status codes, responses, and data.

The API is simulated using **JSON Server**, a tool that allows you to create a mock API with a simple JSON file.

## Tools Used

- **Postman**: API testing tool used for creating the test cases and collections.
- **Newman**: Command-line tool for running Postman collections in an automated manner.
- **JSON Server**: A tool to set up a mock REST API using a simple JSON file for testing purposes.
- **Environment Variables**: Used to store and manage API configuration, such as base URLs and authentication tokens.

## Folder Structure

```plaintext
.
├── collections
│   └── BasicRequests.postman_collection.json      # Postman Collection with test cases
├── environments
│   └── BasicRequests.postman_environment.json     # Postman Environment for storing API variables
├── reports
│   └── newman_report.html      # Newman HTML report generated after running tests
├── db.json                     # JSON Server database file
└── README.md                   # Project documentation
├── TEST_CASES.md               # Detail Test Case documentation

```

## Getting Started

### Prerequisites

- **Install Node.js**: Downlode and install Node.js from [Node.js Download Page](https://nodejs.org/en) (includes npm).
- **Install Postman**: Download and install Postman from [Postman Official Site](https://www.postman.com/).
- **Install JSON Server**: 
  - Install JSON Server globally: 
    ```bash
        npm install -g json-server
    ```
- **Install Newman**:
  - If you don't have Newman installed, you can install it via npm (Node Package Manager).
  - Run the following command in your terminal: 
    ```bash
        npm install -g newman
    ```

- **Clone the repository**:
   ```bash
   git clone https://github.com/shaila1906/API_Testing_with_Postman.git
   cd API_Testing_with_Postman
---

## Running the API with JSON Server

### 1. Set Up JSON Server:
-In the project folder, you will find a ```db.json``` file that acts as the mock database.
- To run the server, open a terminal and execute the following command:

   ```bash
       json-server --watch db.json
    ```

- This will start the mock API at ``` http://localhost:3000 ```.

---

## Running the Tests
### 1. Create the Postman Collection:
- Use Postman to create a collection of your API endpoints and add test cases for each endpoint.
- You can also import the Postman collection (`BasicRequests.postman_collection.json`) into Postman.
- Export the collection as a ```.json``` file.

### 2. Create the Environment:

- In Postman, create an environment to store variables such as API base URLs, user credentials, and any other configurable settings. (As it's a beginner level basic project I only stored API base URLs.)
- Export the environment as a ```.json``` file.

### 3. Execute the Tests Using Newman:
- After setting up the collection and environment, run the tests using the following Newman command:
    ```bash
        newman run your_collection_name.json -e your_environment_name.json -r html --reporter-html-export report.html
    ```

### 4. View the Report:
- Once the tests are completed, an ```HTML``` report will be generated inside the reports folder. You can view the results in your browser by opening ```report.html```.

---
## Test Cases Documentation
The test cases for this project are documented in the `TEST_CASES.md` file. It includes details about the API endpoints, expected responses, and test scenarios.


## Example Environment Variables

You can store the following variables in your Postman environment:
- `baseUserUrl`: The base URL for the User API (e.g., http://localhost:3000/users).
- `baseProductUrl`: The base URL for the Products API (e.g., http://localhost:3000/products).
- Any other variables that you want to re-use.
---

## Example API Request in Postman

### POST /users
```json
{
    "id": "3",
    "name": "Alex Carter",
    "email": "alex.carter@example.com"
    
}
```
### Test Script:

```javascript
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

pm.test("New user is added to the database", function () {
    let jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
	pm.expect(jsonData).to.have.property("name");
	pm.expect(jsonData).to.have.property("email");
    pm.expect(jsonData.name).to.eql("Alex Carter");
});

pm.test("Response contains the new user's ID", function () {
	let jsonData = pm.response.json();
	pm.expect(jsonData.id).to.eql("3");
});

pm.test("Response time is less than 100ms", function () {
	pm.expect(pm.response.responseTime).to.be.below(200);
});

```
---

## Contributing
Contributions are welcome! If you find any issues or want to enhance the project, feel free to submit an issue.

---
## Contact

For any questions, issues, or feedback, feel free to reach out.


