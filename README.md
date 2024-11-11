# Katalon-taskAPI-Dina
Katalon API Integration (JSON)
This project provides an integration with the Katalon API for automating and managing test executions, retrieving test results, and manipulating test cases in Katalon Studio. The Katalon API uses JSON for data exchange, making it easy to interact with programmatically from external systems.

# Table of Contents
* Overview
* Katalon API Authentication
* API Endpoints
  * Post CreateToken
  * Get BookingIds
  * PUT UpdateBooking
  * PATCH PartialUpdateBooking
  * DEL DeleteBooking
* Error Handling

# Overview
Katalon Studio provides a powerful automation solution for web, API, mobile, and desktop testing. The Katalon API allows external tools to trigger tests, manage test cases, and retrieve results. This integration uses JSON to send and receive data, making it simple to automate testing workflows and integrate Katalon into CI/CD pipelines.

# Katalon API Authentication
The Katalon API requires an API Key for authentication. You can obtain the API key from your Katalon Dashboard and use it in your requests to authenticate against the API.

# API Endpoints

  * POST CreateToken
    
Endpoint: POST (https://restful-booker.herokuapp.com/auth)
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

 * Get BookingIds
   
Endpoint: GET [/v1/test-executions/{executionId}/results]
Description: Retrieve the results of a test execution.
Response:
```
{
    "firstname": "Dina",
    "lastname": "Chan",
    "totalprice": 111,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2013-02-23",
        "checkout": "2014-10-23"
    },
    "additionalneeds": "Breakfast"
}
```

  * PUT UpdateBooking
    
Update Test Case
Endpoint: PUT (https://restful-booker.herokuapp.com/booking/:id)
Description: Update an existing test case.
Request Body:
```
{
    "firstname" : "James",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2018-01-01",
        "checkout" : "2019-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
Response:
```
HTTP/1.1 200 OK

{
    "firstname" : "James",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2018-01-01",
        "checkout" : "2019-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```


  * PATCH PartialUpdateBooking
Update Test Case
Endpoint: PATCH (https://restful-booker.herokuapp.com/booking/:id)
Description: Update an existing test case without all data.
Request Body:
```
{
    "firstname" : "James",
    "lastname" : "Brown"
}
```

```
{
    "firstname" : "James",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2018-01-01",
        "checkout" : "2019-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
  * DEL DeleteBooking
    
Delete Test Case
Endpoint: DELETE https://restful-booker.herokuapp.com/booking/1
Description: Delete a specific test case.
Request Body:
```
curl -X DELETE \
  https://restful-booker.herokuapp.com/booking/1 \
  -H 'Content-Type: application/json' \
  -H 'Cookie: token=abc123'
```
Response:
```
HTTP/1.1 201 Created
```


# Error Handling
The Katalon API returns HTTP status codes along with error messages for failed requests.

200 OK: Successful request.
201 Created: Resource successfully created.
400 Bad Request: Invalid request format or missing required parameters.
401 Unauthorized: Invalid API Key or missing authentication.
404 Not Found: Resource not found (e.g., test case or test suite ID).
500 Internal Server Error: Unexpected error on the server.
  
