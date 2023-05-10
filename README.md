https://github.com/aerobean/foodgram-project-react/actions/workflows/main.yml/badge.svg

временный адрес сайта: http://51.250.10.114/


# Foodgram Project

This is the Foodgram project, a web application that allows users to share recipes, follow other users, and create shopping lists based on selected recipes.

The backend is built using Django, Django REST Framework, and PostgreSQL. It provides a REST API that is consumed by the [Foodgram Project React frontend](https://github.com/aerobean/foodgram-project-react/tree/master/frontend).

## Getting Started

To run this project locally, you need to have Docker and Docker Compose installed on your computer. Then, you can follow these steps:

1. Clone this repository to your local machine.
2. Create a `.env` file in the root directory of the project, and add the following variables:

```
POSTGRES_DB=<name of the database>
POSTGRES_USER=<username of the database user>
POSTGRES_PASSWORD=<password of the database user>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<secret key for Django>
DEBUG=<True or False, depending on whether you want debug mode enabled>
ALLOWED_HOSTS=127.0.0.1,localhost
```

3. Start the development server by running `docker-compose up -d --build`.

## Features

The Foodgram Project backend provides the following features:

- Authentication: users can sign up, log in, and log out.
- Profile: users can view and edit their profiles, including their personal information and avatar.
- Recipes: users can create, view, update, and delete recipes. Each recipe includes a title, description, list of ingredients, list of tags, and an image.
- Follow: users can follow other users, and see the list of users they are following.
- Shopping list: users can create a shopping list based on selected recipes, and see the list of ingredients they need to buy.
- API documentation: the backend provides a Swagger/OpenAPI documentation that describes all the endpoints and their parameters.

## CDCI

This project supports Continuous Deployment and Continuous Integration (CDCI) using Docker. The `.github/workflows/main.yml` file contains the configuration for a GitHub Actions workflow that builds a Docker image and pushes it to Docker Hub whenever changes are pushed to the `main` branch.

To use CDCI with Docker, you need to:

- Create a Docker Hub account and repository.
- Add the following secrets to your repository's secrets:

```
DOCKER_USERNAME=<your Docker Hub username>
DOCKER_PASSWORD=<your Docker Hub password>
```

- Modify the `main.yml` file to use your Docker Hub repository name and image tag.

- Collect static files:

```
docker compose exec backend python manage.py collectstatic --no-input
```

- Aplly migrations for the project database:

```
docker-compose exec backend python manage.py makemigrations 
docker-compose exec backend python manage.py migrate
```

- You can use pre-configured set of ingrediens and tags:

```
docker compose exec backend python manage.py load_data
```

- To create the first account for the admin panel use this command:

```
docker-compose exec backend python manage.py createsuperuser
```


## License

This project is licensed under the [MIT License](LICENSE).