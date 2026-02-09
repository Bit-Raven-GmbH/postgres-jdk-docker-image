# Postgres JDK image

A simple docker image that contains postgres and a JDK.

This image is useful if you need to run a database for your Java project in a CI/CD pipeline without hosting the database in a separate container.

## Gitlab

```yml
test:
  stage: test
  image:
    name: mauricemueller/postgres-java:latest
  script:
    - pg_ctl -D /var/lib/postgresql/18/docker -l logfile start
    - psql -c "CREATE USER user WITH PASSWORD 'password' SUPERUSER;"
    - psql -c "CREATE DATABASE database;"
```

Change user, password and database according to your database.

## Build and Push
### Build with GitHub Action
The current image is automatically built on every push outside the main branch. So you get the information if the image
can be built. To push the image you need to run the `Build and Push docker image` GitHub action manually.

You can also trigger the `Build docker image` action manually in the Actions-tab of the repository.

### Build and Push with GitHub Action
1. Go to GitHub Actions
2. Select `Build and Push docker image`
3. Click `Run workflow`
4. Select the branch with the Dockerfile to use
5. Insert the tag you want the new image to have
5. Start workflow

The action automatically builds the current image and pushes it to `docker.io/mauricemueller/postgres-java` with the
specified tag as well as the tag `latest`.

### Build Locally
Run the `build-image-xx`-script matching your operating system and container manager.
