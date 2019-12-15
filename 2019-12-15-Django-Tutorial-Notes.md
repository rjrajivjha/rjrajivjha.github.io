---
layout: post
title: Django : Tutorial - Notes: Part - I
date: 2019-12-12 02:32:20 +0530
description: RESTful API
img: scala.png
tags: [Hackathon]
author: Rajiv Jha
---
December 15, 2019


Docker : 
- Isolate project dependencies from the machine, we are working on
- Lightweight VM
- Consistent Dev environment
- Single image
- Deploy to cloud

Travis CI :
- Automatic run linting and unit test
- CI tool that integrates with github
- Configure Travis CI to run a script.
- It will notify if the build is broken.

Postgres :
- Open source production grade db

What is TDD : 
- You start by isolating a particular code to be tested.
- Test are broken down into 3 stages : 
  - Set up : Create sample db object
  - Execution : Call the code being tested.
  - Assertion : Confirm the expected output.

- Why Tests :
  - Make it easier to change code.
  - Testable, better quality code.
  
- Why TDD :
  - Increase test coverage
  - Ensure tests work
  - Encourages quality code.

- What is docker file ?
  - Docker file is simply a file that contain a list of instructions for docker to build our docker image.
  - Describe all the dependencies, that you need in the project in docker.
  - Go to root of the project, create a file named "Dockerfile"
  - First line is the image, from where you are going to inherit the docker file.
  - You can build image on top of other images.
  - Create our docker file from python3.7 alpine image. It's a lightweight version of docker.
  

  - Setting PYTHONUNBUFFERED=TRUE or PYTHONUNBUFFERED=1 (they are equivalent) allows for log messages to be immediately dumped to the stream instead of being buffered. This is useful for receiving timely log messages and avoiding situations where the application crashes without emitting a relevant message due to the message being "stuck" in a buffer.

  - As for performance, there can be some (minor) loss that comes with using unbuffered I/O. To mitigate this, I would recommend limiting the number of log messages. If it is a significant concern, one can always leave buffered I/O on and manually flush the buffer when necessary.

- What is docker compose?
  It's a tool that allows us to run our docker image easily from our project location.
  It allows us to manage different service that make up our project.
  
- volume allows us to get the update into our project from our image in real time.

- We use docker compose to run a command on our image that contains the django dependency and that will create the project file for our app.

- We run commands using docker compose by typing : 
    docker-compose run <service_name> sh -c "python-admin.py startproect app ."
 
-  Travis CI :
  - Run python unit test
  - Run python linting
  - give email notification
  - Head over to travisci.org
  - Sign up with Github
  - Find your repo and enable the Travis CI
- Travis CI Config file :
  - It tells travis, what to do, everytime we push a change to our project.
  - Create a file in root of project directory, ".travis.yml"
  

- TDD

def add(x,y):
    """Add two numbers"""
    return x+y
def subtract(x,y):
    pass
    
To run tests : docker-compose run app sh -c "python manage.py test"

To run tests and linting together : docker-compose run app sh -c "python manage.py test && flake8"

Happy Learning!

Rajiv Jha :)
 
