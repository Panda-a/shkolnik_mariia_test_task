TC for POST /pet request

TC-1 Create a pet with valid required fields only
<br>Test input: {"name": "Mia", "photoUrls": ["https://сat.jpg"]} 
<br>Expected Result: 200 OK, pet is created

TC-2 Create a pet with all fields
<br>Test input: {"name": "Mia", "photoUrls": ["https://cat.jpg"], "id": 1, "category": {"id": 1, "name": "Cat"},"tags": [{"id": 1, "name": "Ut ut"}], "status": "available"}
<br>Expected Result: 200 OK, pet is created with all attributes

TC-3 Create a pet with empty "tags" array
<br>Test input: {"name": "Mia", "photoUrls": ["https://сat.jpg"], "tags": []}
<br>Expected Result: 200 OK, pet is created without tags

TC-4 Create a pet without "id"
<br>Test input: Enter all fields except id
<br>Expected Result: 200 OK, new id is assigned by system

TC-5 Create a pet with valid "status" values (available, pending, sold)
<br>Test input: 
<br>  1.1 {"name": "Mia", "photoUrls": ["https://cat.jpg"], "status": "available"}
<br>  1.2 {"name": "Mia", "photoUrls": ["https://cat.jpg"], "status": "pending"}
<br>  1.3 {"name": "Mia", "photoUrls": ["https://cat.jpg"], "status": "sold"}
<br>Expected Result: 200 OK, the pet is created and the status is correctly stored in each case

TC-6 Create a pet without "name" (is required)
<br>Test input: {"photoUrls": ["https://сat.jpg"]}
<br>Expected Result: 405 Invalid input

TC-7 Create a pet without "photoUrls" (is required)
<br>Test input: {"name": "Mia"}
<br>Expected Result: 405 Invalid input

TC-8 Create a pet with "name" as an integer
<br>Test input:{"name": 12345, , "photoUrls": ["https://cat.jpg"]}
<br>Expected Result: 405 Invalid input, incorrect data type

TC-9 Create a pet with very long name (ex. 500 characters)
<br>Test input: {"name": "a".repeat(500), "photoUrls": ["https://cat.jpg"]}
<br>Expected Result: 200 OK (if no length limit) or 405 Invalid input (if limit exceeded)

TC-10 Create a pet with duplicate id
<br>Test input: Enter "id" that already existing in system
<br>Expected Result: 409 Conflict or 405 Invalid input

TC-11 Response time under normal load
<br>Test input: Enter all fields 
<br>Expected Result: Response time ≤ 500 ms
