## Metadata
- **ID:** #6
- **Reporter:** Vyskrebstsov O.
- **Severity:** Minor
- **Priority:** Low
- **Type:** Functional / Documentation
- **Environment:** Windows 10 Pro, Google Chrome 146.0.7680.80, API v1.0.0, OAS 3.1

---

## Summary
The `500 Internal Server Error` status code in the `POST /auth/register` documentation is restricted to a single scenario ("Error uploading avatar"), which is misleading.

## Description
In the Swagger/OAS 3.1 documentation, the `500` status code is only described as "Error uploading avatar to File Server". Since `500` is a generic error code representing any unexpected server-side failure, its description should be more universal to cover all potential internal errors.

## Pre-conditions
1. Open the API documentation: <https://healthy-hub-qa.b.goit.study/api-docs/#/>

## Steps to Reproduce
1. Locate the [POST /auth/register](https://healthy-hub-qa.b.goit.study/api-docs/#/Auth/post_auth_register) endpoint.
2. Scroll down to the **"Responses"** section.
3. Observe the description provided for the **500** status code.

## Actual Result
- **Status Code:** 500
- **Description:** "Error uploading avatar to File Server"

## Expected Result
- **Status Code:** 500
- **Description:** "Internal Server Error" (or a broader description that includes various server-side failures).

## Attachments
- [View Evidence](https://drive.google.com/file/d/1Xm5YGteyNHkza4alj5iz-gZrxorEUSai/view?usp=sharing)

## Additional Info
The `500` status code should not be limited to one specific functional part of the request (like the file server). It should remain a general indicator of an unhandled exception on the backend.
