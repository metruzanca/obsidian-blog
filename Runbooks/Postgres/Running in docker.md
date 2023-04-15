# Running pg in docker

This guide will use docker-compose which allows us store the docker commands in a serialized and more easily editable format and give us a few bonus super powers such as dependency/load order.

We'll be using awpl-api's db as an example here.

## Step 1 - Creating the docker-compose.yml
For this container we'll use the official [pg image](https://hub.docker.com/_/postgres) which supplies us with a good template to use with compose as a base.

```yml
version: '3.3'
services:
  db:
    image: postgres                       # Official pg image
    environment:
      POSTGRES_USER: postgres             # same user account
#      POSTGRES_PASSWORD:                # password 
      POSTGRES_HOST_AUTH_METHOD: trust    # enable passwordless
      POSTGRES_DB: dev                    # database name
    ports: 
      - 5432:5432                         # Expose default port
```

## Step 2 - Server side env vars

In awpl-api we have a few env vars that we need to expose

```bash
export CUSTOMCONNSTR_SQL_URL="postgres://awadmin:A5ww9jg9qwCG6dY@localhost:5432/dev"
export SQL_SSL="false"
export FB_APP_ACCESS_TOKEN='...'
```

`SQL_SSL` is set to true by default (for optimal security) but in local we won't be signing certs.
`CUSTOMCONNSTR_SQL_URL` here we pass our custom conn string
(`FB_APP_ACCESS_TOKEN` is specific to awpl-api)

## Step 3 - Run the container

With docker compose we've got a few options.

`docker-compose up`: creates and starts the containers
`docker-compose down`: stops the containers and deletes them
`docker-compose stop`: stops the containers but doesn't delete them
`docker-compose start`: starts containers

If you want to maintain data, I'd recommend using start and stop (after a first `up`). Using down, destroys the container and thus deleting all the data. (Unless a docker volume is used)

For testing/dev work I think this is ideal, `up, stop...start` and using `down` only as a means to clear the data without having to worry about complicated pg commands.

## Step 4 - Run the API

Here you can migrate and run your api and it should use the dockerized pg database.

In awpl-api we just need to run `npm run migrate:latest && npm run dev`

## Step 5 - Aliases (optional)

To use docker-compose, you need to be cd'd into the folder that keeps the docker compose file. Unless of couse you use the `-f` flag which is for specifing a custom compose filename & path.

Personally, since I use a lot of containers. I have the following structure.

(made into a script if you want to use it too)
```bash
mkdir ~/containers/projectName -p;
touch ~/containers/projectName/docker-compose.yml

alias projectName="docker-compose -f ~/containers/projectName/docker-compose.yml"
```

This way from the terminal I can just run `projectName start`

## Step 6 - Profit

Profit.