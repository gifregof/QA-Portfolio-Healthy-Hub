## Metadata
- **ID:** #11
- **Reporter:** Vyskrebstsov O.
- **Severity:** Critical
- **Priority:** High
- **Type:** Functional / Documentation
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The `POST /api/user/food-intake` endpoint returns a `500 Internal Server Error` when sending a string as suggested by the Swagger documentation. The documentation incorrectly defines the request body as a string instead of a structured JSON object.

## Description
There is a severe discrepancy between the documentation and the backend expectations. Swagger UI prompts the user to enter a plain string (e.g., "apple") for the request body. However, the backend expects a JSON object with specific fields (name, calories, etc.). Sending a string causes the JSON parser to crash, resulting in a 500 error.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>
2. Ensure the user is authorized with a valid Bearer token.

## Steps to Reproduce
1. Locate the [POST /api/user/food-intake](https://healthy-hub-qa.b.goit.study/api-docs/#/User/post_user_food_intake) endpoint.
2. Click the **"Try it out"** button.
3. In the request body, enter a plain string (e.g., `"apple"`) as indicated by the current documentation.
4. Click the **"Execute"** button.

## Actual Result
- **Status Code:** 500 Internal Server Error
- **Response Message:** `Unexpected token " in JSON at position 0`
- **Documentation Status:** The Swagger schema for the request body is missing fields like `name`, `calories`, `protein`, etc.

## Expected Result
- **Status Code:** 400 Bad Request (if invalid data is sent).
- **Documentation:** Swagger should provide a clear JSON schema representing the food intake object (including fields: `name`, `calories`, `carbohydrates`, `protein`, `fat`).
- **Behavior:** The server should handle malformed JSON gracefully without a 500 crash.

## Attachments
- [View Evidence](https://drive.google.com/file/d/1gQmTDwrnppR0Uxr9uXTk4p7yyDB7p4Kp/view?usp=sharing)

## Additional Info
- The same documentation error (missing object schema and accepting strings) is present in the `POST /user/food-intake-v2` endpoint.
- This is a **Critical** issue as it prevents developers from knowing the correct data structure required by the API.
