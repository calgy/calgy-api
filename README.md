# Calgy API Server

## Overview

Web server providing an API for managing calendars. Specification of the API
can be found at <https://github.com/calgy/calgy-api-spec>.


## Local Development

### Using Docker

If you have docker installed, the easiest way to get up and running is to
use the docker-compose scripts provided with the app. You do not need to
install elixir or have to worry about any other dependencies.

#### Initial Setup

Run the following only once:
```
docker-compose build
docker-compose start db
docker-compose run web mix ecto.setup
```

#### Starting the Server

Run the following each time you want to start the server:
```
docker-compose up
```

You should now be able to access the server at http://localhost:4000/.

#### Running the Test Suite

If you are already running the web container, it's a little bit faster to
run the test suite using the same container instance by using `exec`:
```
docker-compose exec web mix test
```

Otherwise, you can start a new web container to run the test suite:
```
docker-compose run web mix test
```

#### Database Console

If you need to access a database console:
```
docker-compose exec db psql --user postgres calgy_dev
```

### Manual Setup

You will need to install the following dependencies:

  * Elixir 1.3 or later
  * PostgreSQL 9.5 or later

To start the app:

  * Install dependencies with `mix deps.get`
  * Create and migrate your database with `mix ecto.setup`
  * Start Phoenix endpoint with `mix phoenix.server`

You should now be able to access the server at http://localhost:4000/.

Ready to run in production? Please [check the phoenix deployment guides](http://www.phoenixframework.org/docs/deployment).


## Learn more

  * Official website: http://www.phoenixframework.org/
  * Guides: http://phoenixframework.org/docs/overview
  * Docs: https://hexdocs.pm/phoenix
  * Mailing list: http://groups.google.com/group/phoenix-talk
  * Source: https://github.com/phoenixframework/phoenix
