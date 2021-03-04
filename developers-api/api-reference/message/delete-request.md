---
description: This method allow to delete message to a specific channel.
---

# DELETE Request

#### Before starting, make sure you added **`message_save`** into **`write privileges`**.  See the ****[Application access and privileges](../../get-started/#application-access-and-privileges) ****section.

{% api-method method="post" host="https://api.twake.app" path="/api/v1/messages/remove" %}
{% api-method-summary %}
DELETE Message
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
`Basic base64(public_id:private_api_key)`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="message" type="object" required=true %}
`Require channel_id and content, see the body section`
{% endapi-method-parameter %}

{% api-method-parameter name="group\_id" type="string" required=true %}
`See the group_id and the channel_id section`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
if request is successful, the response should be something like this.
{% endapi-method-response-example-description %}

```
{
    "result": {
        "channel_id": "--", // Channel id
        "id": "--" // Deleted message id
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Body example: 

```text
{
	"group_id": "---", 
	"message": {
		"channel_id": "---",
		"id": "--" // Message id that you want to delete
	}
}
```

