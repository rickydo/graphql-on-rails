Build Rails app:
```
docker-compose run --rm --no-deps web rails new . --force --no-deps --database=postgresql
```

Boot Rails app:
```
docker-compose up --build
```

Create Database in another terminal:
```
docker-compose run --rm web rails db:create
docker-compose run --rm web rails db:migrate
```

To Stop App:
```
docker-compose down
```

Starting the App 
with Gemfile Changes:
```
docker-compose run web bundle install
docker-compose up --build
```

with docker-compose.yml changes:
```
docker-compose up --build
```

without any changes for a rebuild:
```
docker-compose up
```

Tips:
For all rails commands prepend with docker compose
```
rails [command]
```
with:
```
docker-compose run --rm web rails [command]
```

To run if you have a container already running:
```
docker-compose exec
```

To run if you do not have a container running:
```
docker-compose run
```

Automatically remove the docker instance once the command finishes:
```
docker-compose run -rm
```

## builds a container
```
docker-compose build
```

## starts a container thats been built (equivalent to `rails server`)
```
docker-compose up
```

## starts and builds a container
```
docker-compose up --build
```

## runs a one-off instance
```
docker-compose run --rm web [command]
```

## runs a command inside of a running container
## `docker-compose up` needs to be running in another terminal
```
docker-compose exec web [command]
```

## stops the application
```
docker-compose down
```

## Remove orphaned containers as well
```
docker-compose down --remove-orphans
```

## run a bash instance inside of the docker-compose container
## now you can simply run commands like `rails db:migrate` without
## adding `docker-compose run web` before every command
```
docker-compose run --rm web /bin/bash
```

## Things are totally jacked up? Remove all images and containers.
## https://stackoverflow.com/a/52179797
```
docker rm $(docker ps -q -a) -f && docker rmi $(docker images -q) -f
```

# Resource
[Blog Walkthrough](https://blog.konnor.site/rails/getting-started-with-rails-6/)