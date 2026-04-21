# [Bug] 201 Created status code when registering a user with an invalid email format

## Metadata
- **ID:** #16
- **Reporter:** Vyskrebstsov O.
- **Severity:** Major
- **Priority:** Medium
- **Type:** Functional
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The server returns a `201 Created` status code and successfully registers a user even when an invalid email address (containing two "@" symbols) is provided.

## Description
The registration endpoint fails to validate the email format correctly. Providing an email with multiple "@" symbols (e.g., `user@@example.com`) is accepted by the backend, which violates standard email validation rules. Additionally, the Swagger documentation lacks any defined error responses for invalid email inputs.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>

## Steps to Reproduce
1. Locate the [POST /auth/register](https://healthy-hub-qa.b.goit.study/api-docs/#/Auth/post_auth_register) endpoint.
2. Click the **"Try it out"** button.
3. Fill the request body with valid values for all fields except email.
4. In the `"email"` field, enter an address with two "@" symbols (e.g., `test@@mail.com`).
5. Click the **"Execute"** button.

## Actual Result
- **Status Code:** 201 Created.
- **Behavior:** The user is successfully registered with the malformed email address.

## Expected Result
- **Status Code:** 400 Bad Request.
- **Behavior:** Registration should be rejected, and the system should return a validation error stating that the email format is invalid.

## Attachments
- [View Evidence](https://drive.google.com/file/d/1-qEhkeqUeTGkzO1hDgb0vYVXQO-kvMQX/view?usp=sharing)

## Additional Info
The Swagger documentation for this endpoint does not describe expected error codes or response schemas for validation failures related to the email field.
