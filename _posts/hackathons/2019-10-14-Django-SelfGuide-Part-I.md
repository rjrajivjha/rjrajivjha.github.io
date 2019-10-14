---
layout: post
title: Django-SelfGuide - Part I
date: 2019-10-14 02:32:20 +0530
description: Django
img: scala.png
tags: [Hackathon]
author: Rajiv Jha
---
October 14, 2019

Hello!

This series we will learn to do TDD with Django. We will later create a News Platform, following these methodology. 

Django

- Popular web framework of python
- Build web apps rapidly

Features to be used : 
- Django Object Relational Mapper 
  - The ORM provides an easy to use way of converting objects in our api to row in our database.
    Object (API) -> Row (Db)
    
  - for eg. create django model for recipe object and ORM will automatically create recipe table for us.
  
- Django Admin
  - Out of the box admin site
  - Manage models
  - Visualize Database

- Django Rest Framework
  - Extension to django
  - Built in Authentication
  - use viewsets to create structure of API and provide all of necessary endpoint for managing objects.
  - Serializers are used to provide validations on all requests to our API and to help convert JSON object to database models.
  - Browsable API
  
- Docker
  - Virtualization Tool
  - Provide the mechanism for isolating our projects dependencies from the machine it's running on.
  - super light weight VM
  - wrap our project and all of it's dependencies in single image, that can be run on any machine
  - Single Dev environment
  - Used to Deploy to cloud platform

- Travis CI
  - Automate testing and linting
  - automatically run linting and unit test, everytime we make changes to our code.
  - Integrates well with github.
  - CI Tool
  - We can configure Travis CI to run a script everytime we make changes to our code.
  - We will write a script that will run our unit case and linting tool and if either of this fails then travis CI will notify us that the build is broken via an email. 
  - Identify issues early
- Postgres
  - Production grade db
  - Easy to get up and running using Docker
   
Next in the series : What is TDD ?

Happy Learning!

Rajiv Jha :)
 
