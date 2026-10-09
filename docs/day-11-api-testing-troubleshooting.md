## HTTP 404 – Not Found

HTTP 404 indicates that the requested resource could not be found.

### Example

Request:

GET /api/accounts/999

If account 999 does not exist, the application returns:

404 Not Found

### Troubleshooting Approach

If a user reports a 404 error:

1. Verify the HTTP method.
2. Verify the API endpoint.
3. Verify the account ID.
4. Check whether the account exists.
5. Check the Controller mapping.
6. Check the Service logic.
7. Check Repository/database behavior.

### Interview Answer

Question:
"What would you do if an API returns 404?"

Answer:

"I would first verify that the endpoint and resource ID are correct. Then I would check whether the requested resource exists. If it exists, I would trace the request through the Controller, Service, Repository, and database to identify where the request is failing."

### Quick Memory

404 = Resource not found.