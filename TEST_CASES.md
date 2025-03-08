
## Test Cases Included

### 1. User API (`/users`)  
#### 1.1 GET /users (Fetch all users)  
**Test Case ID:** TC_USER_001  
**Method:** GET  
**Endpoint:** `/users`  
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a `GET` request to `/users`  
2. Check if the response status is `200 OK`  
3. Verify the response contains a list of users 
4. Ensure response time is within acceptable limits 
5. Check if response headers include Content-Type: application/json
6. Verify at least one user exists in the list

**Expected Result:**  
✅ API returns a `200 OK` response  

✅ Response contains an array of user objects  

✅ Response time is within acceptable limits

✅ Headers include `Content-Type: application/json`  

✅ At least one user exists


---

#### 1.2 GET /users/{id} (Fetch a specific user)  
**Test Case ID:** TC_USER_002  
**Method:** GET  
**Endpoint:** `/users/{id}`  
**Preconditions:** JSON Server should be running, and the user with id 1 should exist  
**Test Steps:**  
1. Send a `GET` request to `/users/1`  
2. Validate the response status is `200 OK`  
3. Check if the response contains the correct user details 
4. Check if the response format is correct (JSON) 
5. Check for a non-existing user id

**Expected Result:**  
✅ API returns a `200 OK` response  

✅ Response contains user details (ID, Name, Email)  

✅ The response is in JSON format


---

#### 1.3 GET /users/{id} (Fetch a Non-existing user) 
 
**Test Case ID:** TC_USER_003

**Method:** GET

**Endpoint:** `/users/{non-existing id}`  

**Preconditions:** JSON Server should be running  

**Test Steps:**
1. Send a `GET` request to `/users/999`
2. Validate the response status is `404 Not Found`  as user with id 999 doesn’t exist.


**Expected Result:**  
✅  If the user does not exist, return `404 Not Found` 

---


#### 1.4 POST /users (Create a new user) 
 
**Test Case ID:** TC_USER_004  
**Method:** POST  
**Endpoint:** `/users`  
**Request Body:**  
```json
{
  "name": "Alex Carter",
  "email": "alex.carter@example.com"
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``POST`` request with the body to ``/users``
2. Verify response status is 201
3. Validate that a new user is created
4. Check that the response contains the new user’s id
5. Ensure response time is within acceptable limits

**Expected Result:**  
✅ API returns a `201 Created` response  

✅ Response contains new user details (ID, Name, Email)  

✅ Response contains new user id

✅ If the user does not exist, return `404 Not Found`

✅ Response time is within acceptable limits


---


#### 1.5 POST /users (Negative Case01 with no body)
 
**Test Case ID:** TC_USER_005  
**Method:** POST  
**Endpoint:** `/users`  

**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``POST`` request with the empty body to ``/users``
2. Verify response status is 400
3. Validate that a new user is not created

**Expected Result:**  

✅ API returns a `400` response  

✅ No new user is created

---


#### 1.6 POST /users (Negative Case02 with existing email address)
 
**Test Case ID:** TC_USER_006  
**Method:** POST  
**Endpoint:** `/users`  
**Request Body:**  
```json
{
    "name": "John Doe",
    "email": "john@example.com"
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``POST`` request with the body to ``/users``
2. Verify response status is 409
3. Validate that a new user is not created

**Expected Result:**  

✅ API returns a `409` response  

✅ No new user is created


---


#### 1.7 PUT/users/{id} (Update an Existing User - Full Update)
 
**Test Case ID:** TC_USER_007

**Endpoint:** `/users/1`

**Request Body:**  
```json
{
    “name” : “updated John Doe” 
    “email” : “updated@example.com”,
     
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``PUT`` request with the body to ``/users/1``
2. Verify that the response status code is 200 OK.
3. Validate that the response body reflects the updated user details.
4. Ensure the response content type is application/json.
5. Ensure response time is within acceptable limits

**Expected Result:**  
✅  The response code is `200 OK`

✅ The response body reflects the updated user details.

✅ The response content type is application/json

✅ The response time is within acceptable limits

---


#### 1.8 PUT/users/{id} (Update a Non-existing User)
 
**Test Case ID:** TC_USER_008

**Method:** PUT

**Endpoint:** `/users/{non-existing id}` 

**Request Body:**  
```json
{
    
    “name” : “updated John Doe” ,
    “email” : “updated@example.com”
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``PUT`` request with the body to ``/users/999``
2. Verify that the response status code is 404 Not Found.
3. Check the response body for an appropriate error message.


**Expected Result:**  
✅ The response status code is 404

✅ The response body has an appropriate error message

---

#### 1.9 PUT/users/{id} (Update a User with missing fields)

**Test Case ID:** TC_USER_009

**Method:** PUT

**Endpoint:** `/users/{id}`  

**Request Body:**  
```json
{
    
    “name” : “updated Jane Doe” ,
    
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``PUT`` request with the body to ``/users/2``
2. Verify that the response status code is 400 Bad Request
3. Check the response body for an appropriate error message.


**Expected Result:**  
✅ The response status code is 400

✅ The response body has an appropriate error message

---

#### 1.10 PATCH /users/{id} (Partially Update a User)
 
**Test Case ID:** TC_USER_010

**Method:** PATCH

**Endpoint:** `/users/{id}`  

**Request Body:**  
```json
{
   “name” : “updated Alex Carter”
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a PATCH request with the request body.
2. Verify response status is 200 OK.
3. Ensure only specified fields are updated (other fields remain unchanged)
4. Check response contains updated values
5. Ensure response time is within acceptable limits.


**Expected Result:**  
✅ The response status is 200 OK.

✅ Only specified fields are updated (other fields remain unchanged)

✅ The response contains Updated values.

✅ The response time is within acceptable limit.

---


#### 1.11 PATCH /users/{Non-existing id}
 
**Test Case ID:** TC_USER_011

**Method:** PATCH

**Endpoint:** `/users/{Non-existent id}`  

**Request Body:**  
```json
{
   “name” : “updated Alex Carter”
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a PATCH request with the request body.
2. Verify that the response status code is 404 Not Found.
3. Check the response body for an appropriate error message.



**Expected Result:**  
✅ The response status code is 404

✅ The response body has an appropriate error message

---

#### 1.12 PATCH/users/id (with no body) 
 
**Test Case ID:** TC_USER_012

**Method:**  PATCH

**Endpoint:** `/users/{id}`  

**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a PATCH request with no request body.
2. Verify that the response status code is 400 Bad Request
3. Check the response body for an appropriate error message.

**Expected Result:**  
✅ The response status code is 400

✅ The response body has an appropriate error message

---

#### 1.13 DELETE /users/{id} (Delete a user)
 
**Test Case ID:** TC_USER_013

**Method:** DELETE

**Endpoint:** `/users/{id}`   

**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send DELETE request to /users/{id}
2. Verify the response status is 200 OK to confirm the deletion was successful.
3. Make another GET request to /users/{id} with the same user ID.
4. Validate that the response returns 404 Not Found, confirming the user no longer exists.
5. Ensure response time is within acceptable limits.




**Expected Result:**  
✅ User is deleted and response status is 200 OK

✅ GET request’s response is 404 Not Found

✅ The response time is within acceptable limit.

---



### 2. Products API (`/products`)  


#### 2.1 GET /products (Fetch all products)
 
**Test Case ID:** TC_PRODUCTS_001

**Method:** GET

**Endpoint:** `/products`  

**Preconditions:** JSON Server should be running 

**Test Steps:**  
1. Send GET request to /products.
2. Verify response status is 200 OK.
3. Validate response contains a list of products.
4. Check if response headers include Content-Type: application/json 
5. Ensure response time is within acceptable limits.


**Expected Result:**  
✅ The response status is 200 OK.

✅ Response contains an array of product objects  

✅ Headers include `Content-Type: application/json` 

✅ Response time is within acceptable limits

---

#### 2.2 GET /products/{id} (Fetch product by ID)
 
**Test Case ID:** TC_PRODUCTS_002

**Method:** GET

**Endpoint:** `/products/{id}` 

**Preconditions:** JSON Server should be running  

**Test Steps:**  
1. Send a `GET` request to `/products/1`  
2. Validate the response status is `200 OK`  
3. Check if the response contains the correct product details 
4. Check if the response format is correct (JSON) 
5. Check for a non-existing product id


**Expected Result:**  
✅ API returns a `200 OK` response  

✅ Response contains product details (id, name, price)  

✅ The response is in JSON format

✅ If the product does not exist, return `404 Not Found`  

---

#### 2.3 GET /products/{id} (Fetch product by Non-existing ID)
 
**Test Case ID:** TC_PRODUCTS_003

**Method:** GET

**Endpoint:** `/products/{non-existing id}` 

**Preconditions:** JSON Server should be running  

**Test Steps:**  
1. Send a `GET` request to `/products/999`  
2. Validate the response status is `404 Not Found`  


**Expected Result:**  

✅ If the product does not exist, return `404 Not Found`  

---


#### 2.4 POST /products (Create a new product)
 
**Test Case ID:** TC_PRODUCTS_004

**Method:** POST

**Endpoint:** `/products`  

**Request Body:**  
```json
{
  “id” : “3”,
“name” : “Charger”,
“price” : 300
}
```
**Preconditions:** JSON Server should be running  
**Test Steps:** 

1. Send a ``POST`` request with the body to ``/products``
2. Verify response status is 201
3. Validate that a new product is created
4. Check that the response contains the new product’s id
5. Ensure response time is within acceptable limits




**Expected Result:**  

✅ API returns a `201 Created` response  

✅ Response contains new product details (id, name, price)  

✅ Response contains new product’s id

✅ Response time is within acceptable limits 

---


#### 2.5 POST /products (Negative Case01 with no body)
 
**Test Case ID:** TC_PRODUCTS_004  
**Method:** POST  
**Endpoint:** `/products`  
**Preconditions:** JSON Server should be running  
**Test Steps:**  
1. Send a ``POST`` request with the empty body to ``/products``
2. Verify response status is 400
3. Validate that a new user is not created

**Expected Result:**  
✅ API returns a `400` response  
✅ No new product is created

---


#### 2.6 PUT/products/{id} (Update an Existing Product - Full Update)
 
**Test Case ID:** TC_PRODUCT_006

**Method:** PUT

**Endpoint:** `/products/1`  

**Request Body:**  

```json
{   
    “id” : “1”,
    “name” : “updated Laptop” 
    “price” : 1001
     
}
```
**Preconditions:** JSON Server should be running 

**Test Steps:**  
1. Send a ``PUT`` request with the body to ``/products/1``
2. Verify that the response status code is 200 OK.
3. Validate that the response body reflects the updated product details.
4. Ensure the response content type is application/json.
5. Ensure response time is within acceptable limits

**Expected Result:**

✅ The response status code is 200 OK

✅ The response body reflects the updated product details.

✅ The response content type is application/json

✅ The response time is within acceptable limits

---

#### 2.7 PUT/products/{id} (Update a Non-existing Product)
 
**Test Case ID:** TC_PRODUCTS_007

**Method:** PUT

**Endpoint:** `/products/{non-existing id}`  

**Request Body:** 

```json
{
    “id” : “999”,
    “name” : “updated Charger” ,
    “price” : 300
}
```
**Preconditions:** JSON Server should be running 

**Test Steps:**  
1. Send a ``PUT`` request with the body to ``/products/999``
2. Verify that the response status code is 404 Not Found.
3. Check the response body for an appropriate error message.


**Expected Result:**  

✅ The response status code is 404

✅ The response body has an appropriate error message

---

#### 2.8 PUT/products/{id} (Update a Product with missing fields)

**Test Case ID:** TC_PRODUCT_008

**Method:** PUT

**Endpoint:** `/products/{id}` 

**Request Body:**  
```json
{
    
    “name” : “updated Phone” ,
    
}
```
**Preconditions:** JSON Server should be running  

**Test Steps:**  

1. Send a ``PUT`` request with the body to ``/products/3``
2. Verify that the response status code is `400 Bad Request`
3. Check the response body for an appropriate error message.


**Expected Result:**  

✅ The response status code is 400

✅ The response body has an appropriate error message

---


#### 2.9 PATCH /users/{id} (Partially Update a product)
 
**Test Case ID:** TC_PRODUCT_009

**Method:** PATCH

**Endpoint:** `/products/{id}` 

**Request Body:**  
```json
{
   “name” : “updated Phone”
}
```
**Preconditions:** JSON Server should be running 

**Test Steps:**  

1. Send a PATCH request with the request body.
2. Verify response status is 200 OK.
3. Ensure only specified fields are updated (other fields remain unchanged)
4. Check response contains updated values
5. Ensure response time is within acceptable limits.


**Expected Result:**  

✅ The response status is 200 OK.

✅ Only specified fields are updated (other fields remain unchanged)

✅ The response contains Updated values.

✅ The response time is within acceptable limit.

---


#### 2.10 PATCH /products/{Non-existing id}
 
**Test Case ID:** TC_PRODUCT_010

**Method:** PATCH

**Endpoint:** `/products/{Non-existent id}`  

**Request Body:**  
```json
{
   “name” : “updated charger”
}
```

**Preconditions:** JSON Server should be running  

**Test Steps:**  

1. Send a PATCH request with the request body.
2. Verify that the response status code is 404 Not Found.
3. Check the response body for an appropriate error message.



**Expected Result:**  

✅ The response status code is 404

✅ The response body has an appropriate error message

---


#### 2.11 PATCH/products/id (with no body) 
 
**Test Case ID:** TC_PRODUCTS_011

**Method:**  PATCH

**Endpoint:** `/products/{id}`  

**Preconditions:** JSON Server should be running 

**Test Steps:**  

1. Send a PATCH request with no request body.
2. Verify that the response status code is 400 Bad Request
3. Check the response body for an appropriate error message.

**Expected Result:** 

✅ The response status code is 400

✅ The response body has an appropriate error message

---

#### 2.12 DELETE /products/{id} (Delete a product)
 
**Test Case ID:** TC_PRODUCTS_012

**Method:** DELETE

**Endpoint:** `/products/{id}`   


**Preconditions:** JSON Server should be running  

**Test Steps:**  
1. Send DELETE request to /products/{id}
2. Verify the response status is 200 OK to confirm the deletion was successful.
3. Make another GET request to /products/{id} with the same product ID.
4. Validate that the response returns 404 Not Found, confirming the product no longer exists.
5. Ensure response time is within acceptable limits.




**Expected Result:** 

✅ Product is deleted and response status is 200 OK

✅ GET request’s response is 404 Not Found

✅ The response time is within acceptable limit.




