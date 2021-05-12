# Rest APIs

**Prefix**: /internal/services/files/v1/

### Classic upload 

- **POST /companies/:company_id/files/?filename** Upload a file. → This route is call to upload a file when chunk upload is not necessary

    ```javascript
    Response:
    {
        "resource": {
            "company_id": "",
            "id": "uuidA"
        }
    }


### Upload with chunk

- **POST /companies/:company_id/files/?filename** Upload a file. → This route should first be called without data to initialise the entity for multi-chunk, then chunks must be sent on other route below.

    ```javascript
    Response:
    {
        "resource": {
            "company_id": "",
            "id": "uuidA"
        }
    }

    ```

- **POST /companies/:company_id/files/:file_id** Overwrite a file to a company as a user (check user belongs to company) → User can call this if file was not already uploaded → If file already exists only **apps** can do this (users cannot directly overwrite a file)

    ```javascript
    Response:
    {
        "resource": {
            "company_id": "",
            "id": "uuidA"
        }
    }

    ```
    

- **GET /companies/:company_id/files/:file_id** Get file metadatas (check user belongs to company)

    ```javascript
    Response:
    {
      "resource": {
        "company_id": "uuid-v4",
        "id": "uuid-v4",

	    "owner_type": "user" | "application",
	    "owner_id": "uuid-v4",

	    "encryption_key": "",

	    "upload_data": (json){
        "size": number, //Total file size
	    "chunks": number, //Number of chunks
      }

	  "metadata": (json){
        "name": "string", //File name
        "mime": "type/subtype",

        "thumbnail": "" //Url to thumbnail (or set it to undefined if no relevant)
        "width": number, //Thumbnail width (for images only)
        "height": number, //Thumbnail height (for images only)
      }
    }

    ```

- **GET /companies/:company_id/files/:file_id/download** Download a file (check user belongs to company)
- **DELETE /companies/:company_id/files/:file_id** Remove a file (need to be the file owner)



