---
description: >-
  Welcome to the internal documentation section. This chapter is for developers
  working in Twake team or wanting to participate in the project.
---

# 🥇 Get started

> If you are looking for the Developers API of Twake to make plugins, apps or connectors, go here : [Developers API](../developers-api/home.md)

### Start your development server

The development server is a bit different than the production server. The idea is that you want your edited files to be executed by the docker-compose and so you must bind you local code directory to your docker-compose.yml.

#### Step 1 - Use the right docker-compose.yml

```text
cd twake
cp twake/docker-compose.yml.dist.dev twake/docker-compose.yml
```

#### Step 2 - Edit your configuration \(optional\)

You can for instance disable Elastic Search if you don't want to use it on development.

```text
### Backend configuration
cd twake
cp backend/core/app/Configuration/Parameters.php.dist backend/core/app/Configuration/Parameters.php
nano backend/core/app/Configuration/Parameters.php
# Set es.host to false
```

#### Step 3 - Start php and nginx to install dependencies

```text
cd twake
docker-compose up -d php nginx
```

#### Step 4 - Install dependencies

```text
docker-compose exec php php composer.phar install #Could take some time
docker-compose exec nginx yarn install
docker-compose exec nginx yarn build
```

#### Step 5 - Run your local server

```text
cd twake
docker-compose stop
docker-compose up -d
```

You should now be able to access [http://localhost:8000](http://localhost:8000/)

#### Step 6 - Run the frontend with hot-reloading

It's better to have hot reloading while working on frontend. But we do not use the same port for docker and for hot reloading.

```text
cd twake/frontend/
yarn start
```

You should now be able to access [http://localhost:3000](http://localhost:3000/) with hot reloading.

