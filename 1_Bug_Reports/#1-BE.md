ID	#1-BE				
Reporter:	Вискребцов О.	
Severity:	Major	Priority:	High				
Summary:	Код стану 201 при реєстрації користувача з пробілами в паролі									
					
Pre-conditions:					
1	Посилання https://healthy-hub-qa.b.goit.study/api-docs/#/ відкрито в браузері						
Steps to reproduce:					
1	Обрати запит POST/auth/register 				
2	Клікнути на кнопку "Try it out".				
3	Ввести у тіло запиту валідні значення				
4	У ключ "password" ввести пароль з пробілом посередені.				
5	Натиснути на кнопку "Execute".				
Actual result:					
Реєстрація пройшла успішно. Код стану 201					
					
					
Expected result:					
Користувач не зареєстрований. 					
					
					
Attachments:	https://drive.google.com/file/d/1VJ1DYEahF8f8JKOKqIMHUPCoX1eyf5lK/view?usp=sharing				

Additional info:					
Згідно ТЗ в паролі не допустимі пробіли. Однак в документації Swagger відсутній код стану та відповідь на введеня невалідного пароля					
					
