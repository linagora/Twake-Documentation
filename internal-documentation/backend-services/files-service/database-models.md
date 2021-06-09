# Database models

* **files** The main file object in database

  ```javascript
    {
      //Primary key: [["company_id"], "id"]
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

