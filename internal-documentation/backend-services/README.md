---
description: >-
  This page will document all the services implemented in the new NodeJS
  backend. For all the PHP services not yet migrated, please ask us directly on
  https://community.twake.app/
---

# Backend and APIs

Twake follows the micro-services spirit, the idea is to limit interaction between systems, for instance avoid accessing channels information from the file storage system. It will ensure a better and maintainable code.

## Twake Services

As a frontend developer / connector developer to read our APIs, or to understand our data models or just for fun, here is all the details over Twake backend services.

### General

### Services

{% page-ref page="users-and-workspaces-service.md" %}

{% page-ref page="channels-service/" %}

{% page-ref page="messages-service/" %}

{% page-ref page="notifications-service/" %}

## Get started to code in Twake

Want to edit Twake code ? Congratulation ! You participate in the development of a great product 😃

{% page-ref page="twake-service-development/start-working-into-a-service.md" %}

{% page-ref page="twake-service-development/create-a-new-twake-service.md" %}

{% page-ref page="twake-service-development/platform.md" %}

