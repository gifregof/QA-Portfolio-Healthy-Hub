## Metadata
- **ID:** #15
- **Reporter:** Vyskrebstsov O.
- **Severity:** Critical
- **Priority:** High
- **Type:** Functional
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The `POST /user/food-intake` endpoint returns a `500 Internal Server Error` instead of a `401 Unauthorized` when executed via Swagger UI without an authorization token.

## Description
When testing the protected endpoint `POST /user/food-intake` in Swagger UI without a Bearer token, the system fails with a 500 error. This suggests an unhandled exception in how Swagger or the server's security middleware processes missing credentials for this specific method.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>
2. Ensure no authorization token is set (the "Authorize" state is empty).

## Steps to Reproduce
1. Locate the [POST /user/food-intake](https://healthy-hub-qa.b.goit.study/api-docs/#/User/post_user_food_intake) endpoint.
2. Click the **"Try it out"** button.
3. Click the **"Execute"** button without providing a token or request body.
4. Observe the response status code.

## Actual Result
- **Status Code:** 500 Internal Server Error.
- **Behavior:** The server fails to return a standard authorization error.

## Expected Result
- **Status Code:** 401 Unauthorized.
- **Behavior:** The API should consistently return 401 when the required authorization header is missing.

## Attachments
- [View Evidence](https://drive.google.com/file/d/1Qbj6_qi8nWE53EI_RCGlTGHXwrkTuQ1I/view?usp=sharing)

## Additional Info
- This issue is specific to the **Swagger UI** execution. Using **Postman** correctly returns a `401 Unauthorized` status for the same request.
- The same behavior is observed in the following endpoint:
    - [POST /user/food-intake-v2](https://healthy-hub-qa.b.goit.study/api-docs/#/User/post_user_food_intake_v2)
