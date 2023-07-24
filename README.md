# Postgres with pgAdmin and Docker Compose

This project makes it easy to get a local instance of Postgres and pgAdmin up and running using Docker.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

- Docker
- Docker Compose

### Setup

1. Clone this repository to your local machine.
2. Run Docker Compose to create and start the services:

    ```bash
    docker-compose up -d
    ```

3. This will start the PostgreSQL database on port 5432 and pgAdmin on port 5050.

4. Access pgAdmin at [http://localhost:5050](http://localhost:5050).

5. Login using the default email and password provided in the docker-compose file (`admin@admin.com` and `Senha123#`).

6. Get the postgres ip address by running the following command:

    ```bash
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgres
    ```
7. Create a new server in pgAdmin. Right click on `Servers` and select `Create > Server...`.

8. Enter a name for the server and switch to the `Connection` tab.

9. Enter the following values:
    - Host name/address: The ip address obtained in step 6.
    - Port: `5432`
    - Maintenance database: `postgres`
    - Username: `postgres`
    - Password: `postgres`
    - Check `Save password?`

10. Click `Save` to save the server.

You now have a running instance of Postgres and pgAdmin that you can use for your projects!

### Stopping the Services

To stop and remove the containers, networks and volumes defined in the docker-compose file, run the following command:

```bash
docker-compose down
```

Please note that the data stored in Postgres and pgAdmin will persist across container restarts, as long as you don't delete the `postgres-data` and `pgadmin-data` folders.
