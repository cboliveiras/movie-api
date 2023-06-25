Hello! You can set up the platform either with Docker or locally. Choose the method that suits your preferences and requirements :)

## Set Up with Docker

To set up using Docker, follow these steps:

1. Install Docker on your machine if you haven't already. Refer to the Docker documentation for detailed installation instructions: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)

2. Clone the API Test Dimensa repository from GitHub:

```git clone git@github.com:cboliveiras/api-test-dimensa.git```

3. Navigate to the project directory:

```cd api-test-dimensa```

4. Build the Docker image:

```docker-compose build```

5. Run the Docker container:

```docker-compose up```

6. Create the database, run the migrations and create the seeds:

```docker-compose run web rake db:drop db:create db:migrate```

1. The API should now be accessible at [http://localhost:3000](http://localhost:3000)

2. Run the tests:

```docker-compose run web rake spec PGUSER=postgres RAILS_ENV=test```

9. If you want, open a bash session inside the container:

```docker exec -it api-test-dimensa_web_1 bash```

## Set Up Locally

To set up the project locally, follow these steps:

1. Install Ruby 2.7.4 or later on your machine. You can use a version manager like RVM or rbenv to manage your Ruby installations.

2. Clone the API Test Dimensa repository from GitHub:

```git clone git@github.com:cboliveiras/api-test-dimensa.git```

3. Navigate to the project directory:

```cd api-test-dimensa```

4. Install the required gems:

```bundle install```

5. The database.yml file is originally configured to use Docker. If you want to run the application locally, you have to update to:

```
default: &default
  adapter: postgresql
  encoding: unicode

development:
  <<: *default
  database: api-test-dimensa_development

test:
  <<: *default
  database: api-test-dimensa_test
```

Or just comment lines 4-9.

6. Set up the database:

```rails db:create db:migrate```

1. Start the Rails server:

```rails s```

8. The API should now be accessible at [http://localhost:3000](http://localhost:3000)

9. Run all tests:

```rspec spec```

## API Documentation

The Space Code Platform API documentation is available at [API Documentation File](https://github.com/cboliveiras/api-test-dimensa/blob/main/API_Documentation.md). It provides detailed information about all the available endpoints, including request formats, parameters, and responses.

## Postman Collection

