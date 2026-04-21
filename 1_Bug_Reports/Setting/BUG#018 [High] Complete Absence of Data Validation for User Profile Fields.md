## Metadata
- **ID:** #18
- **Reporter:** Vyskrebstsov O.
- **Severity:** High
- **Priority:** High
- **Type:** Functional

---

## Summary
The `/api/auth/settings` endpoint fails to perform sanity checks or data validation on physical and demographic fields. The server accepts biologically impossible values (e.g., age of 25 million years, height of 2500 km) and invalid strings for restricted fields like gender, returning a `200 OK` response and saving this data to the database.


## Environment
* **URL:** https://healthy-hub-qa.b.goit.study/api/auth/settings
* **Method:** `PATCH`
* **Auth:** Valid Bearer Token required
* **Tool:** Postman
* **Date:** April 8, 2026

## Steps to Reproduce
1. Open Postman and target the `PATCH /api/auth/settings` endpoint.
2. Set the `Content-Type` header to `application/json`.
3. Provide the following payload in the request body:
   ```json
   {
     "name": "2345677",
     "gender": "ggg",
     "age": 25000000,
     "height": 2500000,
     "weight": 25000000,
     "activity": 1.5,
     "avatar": "[https://example.com/avatar.png](https://example.com/avatar.png)"
   }
   ```
4. Send the request.

## Actual Result
The server returns 200 OK and echoes the invalid data back in the response body, confirming the data has been accepted and stored.

## Expected Result
- The server should return a 400 Bad Request status code. 
- The response body should contain specific validation error messages for each field (e.g., "Age must be between 1 and 120", "Gender must be Male or Female").

## Attachments
- [View Evidence](https://drive.google.com/file/d/174gA6JeQVdeuZFNICVzjXKx5gTU7JZmD/view?usp=sharing)
