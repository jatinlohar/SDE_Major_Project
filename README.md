﻿# SDE Major Project

This is an example of web application comprising of several components communicating to each other. In other words, this is an example of microservice app. Why is it better than many other examples? Well, because these microservices are written in different languages. This approach gives you flexibility for running experiments in polyglot environment.

The app itself is a simple TODO app that additionally authenticates users. I planned to add some admin functionality, but decided to cut the scope and add it later if needed.

## Components

1. [Frontend](/frontend) part is a Javascript application, provides UI. Created with [VueJS](http://vuejs.org)

2. [Authorization App](/authorization_app) is written in Go and provides authorization functionality. Generates JWT tokens to be used with other APIs.

3. [TODO APP](/ToDo_app) is written with NodeJS, provides CRUD functionality ove user's todo records. Also, it logs "create" and "delete" operations to Redis queue, so they can be later processed by [Log Message Processor](/message_logger).

4. [User APP](/users-api) is a Spring Boot project written in Java. Provides user profiles. Does not provide full CRUD for simplicity, just getting a single user and all users.
5. [Log Message Processor](/message-logger) is a very short queue processor written in Python. It's sole purpose is to read messages from Redis queue and print them to stdout
6. [Zipkin](https://zipkin.io). Optional 3rd party system that aggregates traces produced by other components.

Take a look at the components diagram that describes them and their interactions.
![Screenshot 2024-11-15 225447](https://github.com/user-attachments/assets/e12e57b1-8172-46a8-9605-bf83bfe7bbb1)


## Use cases

- Evaluate various instruments (monitoring, tracing, you name it): how easy they integrate, do they have any bugs with different languages, etc.

## How to start

The easiest way is to use `docker-compose`:

```
docker-compose up --build
```

Then go to http://127.0.0.1:8080 for web UI. [Zipkin](https://zipkin.io) is available on http://127.0.0.1:9411 by default.
