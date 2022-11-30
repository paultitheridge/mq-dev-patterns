# Using Docker Compose to deploy IBM MQ Queue Manager
These yaml and .env files provide a starter set which
can be used to deploy an running IBM MQ Queue Manager
container using Docker Compose.

## External Storage
External storage will allow queues, persistent messages,
and logs to persist across container outages.

Initialise the external storage by running

````
docker compose -f mq-init-compose.yaml up
````

The container will start, initialise the storage, and then stop.

## App and Admin credentials
The App and Admin use credentials are held in the `.env` file. Edit the file to set the passwords.

## Queue Manager
Start the queue manager by running

````
docker -f docker-compose.yaml up
````

If you see the start fails with the following error:

````
WARNING The "APP_PASSWORD" variable is not set. Defaulting to a blank string.
WARNING The "ADMIN_PASSWORD" variable is not set. Defaulting to a blank string.
````

then you have not set the App and Admin passwords in the `.env` file.

## Stopping the container
Stop the queue manager container by running

````
docker -f docker-compose.yaml down
````