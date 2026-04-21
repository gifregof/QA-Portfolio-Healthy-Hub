## Metadata
- **ID:** #3
- **Reporter:** Vyskrebstsov O.
- **Severity:** Major
- **Priority:** High
- **Type:** Functional
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The `PATCH /auth/settings` endpoint returns a `400 Bad Request` error when attempting to update the "goal" field, even though this field is defined in the Swagger documentation.

## Description
There is a discrepancy between the API implementation and the OAS 3.1 documentation. While the Swagger UI includes the "goal" field and provides "Maintain" as an example value, the server rejects requests containing this field. Other fields in the same endpoint are updated successfully.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>
2. The user must be authorized with a valid Bearer token.

## Steps to Reproduce
1. Locate the [PATCH /auth/settings](https://healthy-hub-qa.b.goit.study/api-docs/#/Auth/patch_auth_settings) endpoint.
2. Click the **"Try it out"** button.
3. In the request body, provide a valid value for the `"goal"` field (e.g., `"Maintain"`).
4. Click the **"Execute"** button.

## Actual Result
- **Status Code:** 400 Bad Request
- **Response Body:** `{"message": "Goal is not allowed"}`

## Expected Result
- **Status Code:** 200 OK
- **Response Body:** `{"message": "Successful operation"}`
- **Behavior:** The user's goal should be successfully updated in the system.

## Attachments
- [View Evidence](https://drive.google.com/file/d/1izlWynr9S0sxAGevQvdvO_WqROvACtEJ/view?usp=sharing)

## Additional Info
The issue is isolated specifically to the "goal" field. All other user settings fields are processed correctly by the API.
