## Metadata
* **ID:** #1
* **Reporter:** Vyskrebstsov O.
* **Severity:** Major
* **Priority:** High
* **Type:** Functional
* **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The server returns a **201 Created** status code and successfully registers a user even if the password contains spaces, which violates the technical requirements.

## Description
According to the technical specifications, spaces are not allowed in passwords. However, the system currently accepts them during registration. Additionally, the Swagger documentation does not define the expected error response for invalid password formats.

## Pre-conditions
1.  Navigate to the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>

## Steps to Reproduce
1.  Locate the [POST /auth/register](https://healthy-hub-qa.b.goit.study/api-docs/#/Auth/post_auth_register) endpoint.
2.  Click the **"Try it out"** button.
3.  Fill the request body with valid data.
4.  In the `"password"` field, enter a password containing at least one space (e.g., `"pass word123"`).
5.  Click the **"Execute"** button.

## Actual Result
> **Status Code:** 201 Created  
> **Result:** The user is successfully registered in the system.

## Expected Result
> **Status Code:** 400 Bad Request  
> **Result:** Registration should be rejected, and the system should return a validation error regarding the invalid password format.

## Attachments
* [View Evidence](https://drive.google.com/file/d/1VJ1DYEahF8f8JKOKqIMHUPCoX1eyf5lK/view?usp=sharing)

## Additional Info
* The Swagger documentation (OAS 3.1) is missing the error schema for invalid password input.
