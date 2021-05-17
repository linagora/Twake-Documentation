# REST APIs

**Prefix**: /internal/services/files/v1/

## General

* **GET /companies/:company\_id/files/:file\_id** Get file metadatas \(check user belongs to company\)

  ```javascript
    Response:
    {
      "resource": {
        "company_id": "uuid-v4",
        "id": "uuid-v4",

        "owner_type": "user" | "application",
        "owner_id": "uuid-v4",

        "encryption_key": "",

        "upload_data": (json) {
            "size": number, //Total file size
            "chunks": number, //Number of chunks
        }

        "metadata": (json) {
            "name": "string", //File name
            "mime": "type/subtype",

            "thumbnail": "" //Url to thumbnail (or set it to undefined if no relevant)
            "width": number, //Thumbnail width (for images only)
            "height": number, //Thumbnail height (for images only)
        }
      }
    }
  ```

* **GET /companies/:company\_id/files/:file\_id/download** Download a file

## Classic upload

To upload a single file, you must call this route and put the file binary data into a "file" multipart section.

* **POST /companies/:company\_id/files** Upload a file. → This route is call to upload a file when chunk upload is not necessary

  \`\`\`javascript Response: { "resource": { "company\_id": "", "id": "uuidA" } }

## Upload with chunk

To upload a file in multiple chunk you must first initial the file itself, and then upload into the file.

The file initialisation and following upload calls takes this parameters as **a query string**:

* **filename**: string, file name
* **type**: string, mime type for the file
* **totalChunks**: number, total number of chunk to be uploaded
* **totalSize**: number, sum of every chunk size \(total file size\)
* **chunkNumber**: number, current chunk uploaded, set it to undefined during file creation process.
* **POST /companies/:company\_id/files/?filename...** Upload a file. → This route should first be called without data to initialise the entity for multi-chunk, then chunks must be sent on other route below.

  ```javascript
    Response:
    {
        "resource": {
            "company_id": "",
            "id": "uuidA"
        }
    }
  ```

* **POST /companies/:company\_id/files/:file\_id/?totalChunks...** Overwrite a file to a company as a user \(check user belongs to company\) → User can call this if file was not already uploaded → If file already exists only **apps** can do this \(users cannot directly overwrite a file\)

  ```javascript
    Response:
    {
        "resource": {
            "company_id": "",
            "id": "uuidA"
        }
    }
  ```

