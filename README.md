# LadyBug - Productivity and issue tracking for individuals and small teams.

LadyBug is being developed as an exercise in learning software development infrastructure. The app itself is a simple project management tool - users can create projects where tasks are managed on a Kanban board and invite other users to join the project.

My focus in building this application is to expand my knowledge on devops topics such as production deployments and automated testing.

I'm using the following technologies to accomplish the goals of this project:
- Node, Express, React
- Docker / Docker-Compose
- Nginx

The project will be deployed to AWS.

## Dependencies:
- Docker
- Docker-Compose
- OpenSSL (to generate local certificate)

## To run locally in development mode:
- Create a /certs directory in the project root. This will need to contain a key.pem file and certificate.pem file to enable SSL and allow http cookies to be sent between the client and the server. Learn how to generate local SSL certificates [here](https://devcenter.heroku.com/articles/ssl-certificate-self).

- Create a .env file in the project root. This will need to define the following environment variables:
```
    PORT=5001
    CLIENT_URL='https://localhost'
    SERVER_URL='https://localhost:5001'
    POSTGRES_USER=postgres
    POSTGRES_PASSWORD= (choose a password)
    POSTGRES_DB=ladybug_dev
    POSTGRES_PORT=5432
    POSTGRES_HOST=172.17.0.1
    JWT_SECRET= (obtain a secure 128-bit secret or simply define as 'dev_secret')
    JWT_EXPIRES_IN='24h'
    REFRESH_EXPIRES_IN='1w'
    NODE_ENV=development
```
- Run the following command:

```
docker-compose -f docker-compose.dev.yml watch
```
This selects the development Compose file and watches the client and server directories for code changes.

- Visit https://localhost in your browser.