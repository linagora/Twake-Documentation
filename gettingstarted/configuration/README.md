---
description: More details about Twake configuration.
---

# ⚙️ Configuration

### Detach the configuration and start using your own

Each configuration file is optional, if not given, Twake will fallback to default configuration.

#### Backend configuration

You can find an example of Twake configuration \(default configuration\) here: [https://github.com/TwakeApp/Twake/blob/main/twake/backend/core/app/Configuration/Parameters.php.dist](https://github.com/TwakeApp/Twake/blob/main/twake/backend/core/app/Configuration/Parameters.php.dist)

Copy the content of this file and put it in `[docker-compose.yml location]/configuration/backend/Parameters.php`

> **Tip:** you can put a 'cert' directory with apns.cert keys \(mobile push notifications\) beside the Parameters.php file.

#### Frontend configuration

You can find an example of Twake configuration \(default configuration\) here: [https://github.com/TwakeApp/Twake/blob/main/twake/frontend/src/app/environment/environment.ts.dist](https://github.com/TwakeApp/Twake/blob/main/twake/frontend/src/app/environment/environment.ts.dist)

Copy the content of this file and put it in `[docker-compose.yml location]/configuration/frontend/environment.ts`

Now, your installation will use this configuration. **Each time you change the configuration**, restart your docker container like this: 

```text
docker-compose restart
docker-compose exec nginx yarn build #If you have custom frontend configuration
```

The subpages will talk about each configuration blocks.

