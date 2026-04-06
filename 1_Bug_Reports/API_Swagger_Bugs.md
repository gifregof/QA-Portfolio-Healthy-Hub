### Bug ID: 26 - Contract Violation (Swagger vs Backend)
**Severity:** Critical | **Priority:** High

**Summary:** Swagger ігнорує введене значення "count" і відправляє запит GET /user/recommended-food без параметрів (що призводить до 400 Bad Request).

**Steps to Reproduce:**
1. Відкрити Swagger UI та авторизуватися.
2. Обрати GET `/user/recommended-food` та ввести `5` у поле `count`.
3. Натиснути Execute.

**Actual Result:**
Запит відправляється без параметра `count` у URL. У вкладці Network фіксується відправка базового URL. Сервер повертає `400 Bad Request`.

**Root Cause Analysis:**
Проблема в конфігурації OpenAPI. Параметр `count` помилково вказано як `path` (без плейсхолдера `{count}` у маршруті), хоча бекенд очікує його як `query` параметр.
