# Katalon-taskAPI-Dina
Katalon API Integration (JSON)
This project provides an integration with the Katalon API for automating and managing test executions, retrieving test results, and manipulating test cases in Katalon Studio. The Katalon API uses JSON for data exchange, making it easy to interact with programmatically from external systems.

# Table of Contents
* Overview
* Katalon API Authentication
* API Endpoints
  * Run Test Suite
  * Get Test Results
  * Create Test Case
  * Update Test Case
  * Delete Test Case
  * List Test Cases
* Request & Response Format
* Error Handling
* Authentication
* Contributing
* License

# Overview
Katalon Studio provides a powerful automation solution for web, API, mobile, and desktop testing. The Katalon API allows external tools to trigger tests, manage test cases, and retrieve results. This integration uses JSON to send and receive data, making it simple to automate testing workflows and integrate Katalon into CI/CD pipelines.

# Katalon API Authentication
The Katalon API requires an API Key for authentication. You can obtain the API key from your Katalon Dashboard and use it in your requests to authenticate against the API.

# API Endpoints
  * Run Test Suite
Endpoint: POST /v1/test-suites/{testSuiteId}/run
Description: Trigger the execution of a test suite in Katalon.
Request Body:
```
{
    "username" : "admin",
    "password" : "password123"
}
```

Response:
```
HTTP/1.1 200 OK

{
    "token": "abc123"
}
```

