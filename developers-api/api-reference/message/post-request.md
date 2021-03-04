---
description: This method allow to send message to a specific channel.
---

# POST Request

#### Before starting, make sure you added **`message_save`** into **`write privileges`**.  See the ****[Application access and privileges](../../get-started/#application-access-and-privileges) ****section.

{% api-method method="post" host="https://api.twake.app" path="/api/v1/messages/save" %}
{% api-method-summary %}
POST message
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
`Basic base64(public_id:private_api_key)`
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="message" type="object" required=true %}
`Require channel_id and content, see the Body section`
{% endapi-method-parameter %}

{% api-method-parameter name="group\_id" type="string" required=true %}
`See the group_id and channel_id section`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
If request is successful, the response should be something like this.
{% endapi-method-response-example-description %}

```
{
    "object": {
        "id": "--", // Message Id
        "channel_id": "--", // Channel
        "parent_message_id": "--", // Thread id
        "sender": null, // User who send the message
        "application_id": "--", // Application who send the message
        "edited": false, 
        "pinned": null,
        "hidden_data": null,
        "reactions": [],
        "modification_date": 1598518289, // Last modification date
        "creation_date": 1598518289, // Creation date
        "content": "Hello !", // Object (see Twacode) or string
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Body example: 

```text
{
	"group_id": "--",
	"message": {
		"channel_id": "--",
		"content": "Hello, this is my first message !",
		"_once_ephemeral_message": false // Set true if you want this message ephemeral
	}
}
```

