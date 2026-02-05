# Postgres JDK image

A simple docker image that contains postgres and a JDK - mainly for usage in CI/CD pipelines.

This image is useful if you need to run a database in a CI/CD pipeline.

To use it you need following code in your Gitlab CI:

```yml
test:
  stage: test
  image:
    name: mauricemueller/postgres-java:latest
    docker:
      user: postgres
  script:
    - initdb
    - pg_ctl -D /var/lib/postgresql/18/docker -l logfile start
    - psql -c "CREATE USER user WITH PASSWORD 'password' SUPERUSER;"
    - psql -c "CREATE DATABASE database;"
```
Exchange user, password and database according to your database.