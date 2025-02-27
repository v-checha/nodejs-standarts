# 📖 API Design

**Resource-Oriented Design:**

* **Concept:** Structure your API around resources (entities) relevant to your application domain. Each resource represents a distinct data type and exposes a set of operations (CRUD) through the API.
* **Example:** In an e-commerce application, resources might be `products` (containing product details like name, price, description) and `orders` (with order details like items, user, and total amount).

**RESTful Principles:**

* **Concept:** Consider adhering to RESTful principles whenever possible. This ensures consistent design patterns and simplifies API usage.
  * Stateless interactions (server doesn't store client state between requests).
  * Use of HTTP methods (GET, POST, PUT, DELETE) for CRUD operations.
  * Consistent use of resources and URIs for accessing and manipulating data.
* **Example:**
  * `GET /products` retrieves a list of all products.
  * `POST /products` creates a new product with data provided in the request body.
  * `PUT /products/:id` updates an existing product with the specified ID.
  * `DELETE /products/:id` deletes a product with the specified ID.
*   A JSON object **must** be at the root of every JSON:API request and response document containing data. This object defines a document’s “top level”.

    A document **must** contain at least one of the following top-level members:

    * `data`: the document’s “primary data”.
    * `error`: an array of error objects.
    * `meta`: a meta object that contains non-standard meta-information

**API Naming Conventions:**

* **Concept:** Employ clear and descriptive naming conventions for API endpoints, resources, parameters, and response objects.
* **Example:**
  * Endpoints: `/users`, `/products/reviews`
  * Resources (in response body): `user`, `review`
  * Parameters: `name`, `price`, `rating` (descriptive parameter names)

**Versioning:**

* **Concept:** Implement a versioning strategy to manage API changes over time.
* **Example:** URL-based versioning: `/api/v1/users` or header-based versioning: `Accept: application/json; version=1`.

**Authentication and Authorization:**

* **Concept:** Implement authentication to control access and authorization to restrict access based on user roles or permissions.
* **Example:** JWT (JSON Web Token) based authentication for access control. Roles stored in the JWT payload can be used for authorization checks on specific API endpoints.

**Error Handling:**

* **Concept:** Design a consistent error handling strategy with informative error responses and appropriate HTTP status codes.
* **Example:**
  * `400 Bad Request` - for invalid data in request body.
  * `404 Not Found` - for requesting a non-existent resource.
  * Response body containing error message: `{ "error": "Product not found with ID: 123" }`

**Documentation:**

* **Concept:** Provide comprehensive API documentation using tools like Swagger or OpenAPI Specification (OAS) to generate interactive API documentation.
* **Example:** Utilize Swagger UI to provide an interactive interface for developers to explore API endpoints, parameters, and expected responses.

**Additional Considerations:**

* **Rate Limiting:** Limit API requests per user or IP address to prevent abuse.
* **Pagination:** For large datasets, return results in smaller chunks using query parameters like `limit` and `offset`.
* **Filtering and Sorting:** Allow users to filter and sort data using query parameters like `category` or `price[gt]=100` (greater than 100).
* **Testing:** Integrate API testing into your overall testing strategy using frameworks like Jest or Mocha to ensure API functionality works as expected.
