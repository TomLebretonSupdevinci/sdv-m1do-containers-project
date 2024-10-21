# Sup de Vinci - Containers module project

# Stack DEVELOPMENT

Clone the repository on its machine : `git clone https://github.com/TomLebretonSupdevinci/sdv-m1do-containers-project.git`

To run the stack docker containing both containers (api and front) run the command: `cd sdv-m1do-containers-project && docker compose up`. It will be run the dev stack. 

You must be in the repertoire of your git repository is located the docker-compose.yaml

Connect to webpage : http://localhost:3000
Connect to apipage : http://localhost:8000

# Stack PRODUCTION

To put into production you can use a docker-compose file like this :

``
yaml

services:
  api:
    image: tomlbt/rustapilebretontomsdv:tagname
    ports:
      - "80:80"
    volumes:
      - ./sdv-api:/app

  web:
    image: tomlbt/frontendlebretontomsdv:tagname
    ports:
      - "3000:3000"
    volumes:
      - ./sdv-web:/app
    environment:
      - API_URL=http://api

``

Connect to webpage : http://localhost:3000
Connect to apipage : http://localhost:80

The website request the URL http://localhost/jokes/random in http and display a random joke on the webpage.

# CI/CD Pipeline

When you make a modification and push on the repo, github execute these tasks :

- Retrieval of source code on the repositorie.
- Log in to Docker Hub with the variables in the SECRET part of the repositorie.
- Build API Image
- Build WebPage Image
- Push API Image into the DockerHub Repo
- Push WebPage Image into the DockerHub Repo

These Images can now be used to deploy the Production Stack


