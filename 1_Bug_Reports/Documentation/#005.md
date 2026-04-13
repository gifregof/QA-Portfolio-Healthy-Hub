# [Minor] Missing "token" field in GET /auth/current response body

## Metadata
- **ID:** #5
- **Reporter:** Vyskrebstsov O.
- **Severity:** Minor
- **Priority:** Medium
- **Type:** Functional
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The `GET /auth/current` endpoint does not return the "token" field in the response body, although it is explicitly defined in the Swagger documentation (Example Value).

## Description
There is a discrepancy between the API implementation and the OAS 3.1 documentation. The documentation indicates that the response should include a "token" field, but the actual JSON response from the server omits it.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>
2. Ensure the user is authorized with a valid Bearer token.

## Steps to Reproduce
1. Locate the [GET /auth/current](https://healthy-hub-qa.b.goit.study/api-docs/#/Auth/get_auth_current) endpoint.
2. Click the **"Try it out"** button.
3. Click the **"Execute"** button.
4. Compare the actual JSON in the **"Response body"** section with the schema provided in the **"Example Value"** section.

## Actual Result
- The `"token"` field is missing from the response body.
- Only other user data (e.g., email, name) is returned.

## Expected Result
- The response body should match the documentation.
- The `"token"` field should be present in the response (if required by logic) or removed from the Swagger schema to avoid confusion.

## Attachments
- [View Evidence](https://drive.google.com/file/d/1ZKk5aPtRq19nEjdzG3FlZ9HUQWblHmzd/view?usp=sharing)

## Additional Info
Documentation must strictly reflect the actual API behavior. If the token is not intended to be returned in this request, the documentation should be updated to remove the field.
