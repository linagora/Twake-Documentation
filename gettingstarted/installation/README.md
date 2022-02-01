---
description: How to install Twake
---

# 🏗 Install on your server

## Use Twake in SaaS

You can test or use Twake in our SaaS : [chat.twake.app](https://chat.twake.app)

## Run Twake in your server

First you'll need to [install docker and docker-compose](https://docs.docker.com/compose/install/).

Then you can install Twake on your server with this command

```
git clone https://github.com/TwakeApp/Twake.git
cd Twake/twake
docker-compose -f docker-compose.onpremise.mongo.yml up -d
```

### What's next ?

If you kept the default configuration, you can simply follow the signup steps, no email verification is required by default so you will get into Twake right after the signup steps.

## Ship Twake in production

See how to [manage configuration](../configuration/). And then how to [update security keys](../configuration/security.md), and finally how to use your [custom domain](../configuration/custom-domain-and-https/).

### Update Twake

```
docker-compose stop
docker-compose rm #Remove images (not volumes so your data is safe)
docker-compose pull #Get new images
docker-compose up -d
docker-compose exec nginx yarn build #If you have custom frontend configuration
```

## Requirements and scalability

Currently you'll need at least a **2 cpu + 4 gb of ram** machine for **20-50 users** depending on their usage and with ElasticSearch disabled.

If you enable ElasticSearch, use two machines, or limit the cpu/ram dedicated to it and use a larger machine (at least 2gb of ram and 1 cpu dedicated to ES for 20-50 users).

If you need to deploy Twake for more users, you can use only one big machine up to 500 users (Will need something like **12 cpu and 32go of ram**), then you'll need to use multiple nodes.

{% hint style="info" %}
We deployed Twake on production for companies of 10 to 50 users in a single node. We also deployed Twake in a scalable mode and we support currently thousands of concurrent users.

If you deploy Twake in your own company we would love to have your feedback here [https://github.com/TwakeApp/Twake/issues/289](https://github.com/TwakeApp/Twake/issues/289) to improve our requirements documentation.
{% endhint %}

Now if you want to scale with Twake and support thousand of users, click on the link below :

{% content-ref url="scale-with-twake.md" %}
[scale-with-twake.md](scale-with-twake.md)
{% endcontent-ref %}
