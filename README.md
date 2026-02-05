# Postgres JDK image

A simple docker image that contains postgres and a JDK.

This image is useful if you need to run a database for your Java project in a CI/CD pipeline without hosting the database in a separate container.

## Gitlab

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

Change user, password and database according to your database.
