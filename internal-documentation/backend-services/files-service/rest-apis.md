# Rest APIs

**Prefix**: /internal/services/files/v1/

- **POST /companies/:company_id/files** Upload a file. → This route should first be called without data to initialise the entity for multi-chunk, then chunks must be sent on other route below.

    ```json
    Response:
    {
    	"resource": {
    		"company_id": "",
        "id": "uuidA"
      }
    }

    ```

- **POST /companies/:company_id/files/:file_id** Overwrite a file to a company as a user (check user belongs to company) → User can call this if file was not already uploaded → If file already exists only **apps** can do this (users cannot directly overwrite a file)

    ```json
    Response:
    {
    	"resource": {
    		"company_id": "",
        "id": "uuidA"
      }
    }

    ```

- **GET /companies/:company_id/files/:file_id** Get file metadatas (check user belongs to company)

    ```json
    Response:
    {

    }

    ```

- **GET /companies/:company_id/files/:file_id/download** Download a file (check user belongs to company)
- **DELETE /companies/:company_id/files/:file_id** Remove a file (need to be the file owner)
