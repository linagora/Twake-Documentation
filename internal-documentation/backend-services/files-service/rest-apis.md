---
description: Rest api for files
---

# REST APIs

**Prefix**: /internal/services/files/v1/

## General

{% api-method method="get" host="/internal/services/files/v1" path="/:company\_id/files/:file\_id" %}
{% api-method-summary %}
Get file metadata \(check user belongs to comapny\)
{% endapi-method-summary %}

{% api-method-description %}
This route is called to get the metadata related to the `file_id` mentioned in the URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Response:
  {
    "resource": {
        "company_id": "uuid-v4",
        "id": "uuid-v4",
        "application_id": "string",
        "created_at": "number",
        "encryption_key": "",
        "metadata": {
            "name": "string",
            "mime": "string"
        },
        "thumbnails": [
            {
                "index": number,
                "id": "string,
                "size": number,
                "type": "string",
                "width": number,
                "height": number
            }
        ],
        "updated_at": number,
        "upload_data": {
            "size": number,
            "chunks": number
        },
        "user_id": "uuid-v4"
    }
  }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="/internal/services/files/v1" path="/companies/:company\_id/files/:file\_id/download" %}
{% api-method-summary %}
Download a file 
{% endapi-method-summary %}

{% api-method-description %}
This route is called to download the file related to the `file_id` mentionned in the URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="/internal/services/files/v1" path="/companies/:company\_id/files/:file\_id/thumbnails/:id" %}
{% api-method-summary %}
Download thumbnails
{% endapi-method-summary %}

{% api-method-description %}
This route is called to download the thumbnail related to the `file_id` mentionned in the URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

\*\*\*\*

{% api-method method="delete" host="/internal/services/files/v1" path="/companies/:company\_id/files/:file\_id" %}
{% api-method-summary %}
Delete a file
{% endapi-method-summary %}

{% api-method-description %}
This route is called to delete the file related to the `file_id` mentionned in the URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Classic upload

To upload a single file, you must call this route and put the file binary data into a "file" multipart section.

{% api-method method="post" host="/internal/services/files/v1" path="/companies/:company\_id/files?thumbnail\_sync=1" %}
{% api-method-summary %}
Upload a file 
{% endapi-method-summary %}

{% api-method-description %}
This route is called to upload a file when chunk upload is not necessary.  
Thumbnail\_sync: when set then backend will wait up to 10 seconds for preview to be generated before reply.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="thumbnail\_sync" type="boolean" required=false %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="File " type="object" required=false %}
The file which will be uploaded
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
response : 
  {
    "resource": {
        "company_id": "uuid-v4",
        "metadata": {
            "name": "string",
            "mime": "string"
        },
        "thumbnails": [],
        "application_id": string,
        "upload_data": {
            "size": number,
            "chunks": number
        },
        "id": "uuid-v4",
        "updated_at": number,
        "created_at": number
  }
}
  
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Upload with chunk

To upload a file in multiple chunk you must first initial the file itself, and then upload into the file.

The file initialization and following upload calls takes this parameters as **a query string**:

* **filename**: string, file name
* **type**: string, mime type for the file
* **total\_chunks**: number, total number of chunk to be uploaded
* **total\_Size**: number, sum of every chunk size \(total file size\)
* **chunk\_number**: number, current chunk uploaded, set it to undefined during file creation process.
* **thumbnail\_sync:** when set then backend will wait up to 10 seconds for the preview to be generated before to reply.

{% api-method method="post" host="/internal/services/files/v1" path="/companies/:company\_id/files/?filename..." %}
{% api-method-summary %}
Upload a file with chunk
{% endapi-method-summary %}

{% api-method-description %}
This route should first be called without data to initialise the entity for multi-chunk, then chunks must be sent on other route below
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="/internal/services/files/v1" path="/companies/:company\_id/files/:file\_id/?totalChunks..." %}
{% api-method-summary %}
Overwrite a file 
{% endapi-method-summary %}

{% api-method-description %}
Overwrite a file   
\(check user belongs to company\)  
User can call this if the file was not already uploaded. If file already exist only apps can do this \(users cannot directly overwrite a file\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

