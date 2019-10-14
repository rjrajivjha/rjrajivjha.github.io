---
layout: post
title: Django SelfGuide - Part II
date: 2019-10-14 02:32:20 +0530
description: DJango - Test Driven Development
img: scala.png
tags: [Hackathon]
author: Rajiv Jha
---
October 14, 2019

Hello!

When writing a software, it's important to write unit test cases with your code. This post help us understand the Test driven development.

- It check that your code does exactly what it's supposed to.(Check that your code works.)

- You start by isolating a particular piece of code to be tested.
- This could be a function or a class.
- In our case, most of the test we will write will be making actual API calls to our endpoints, knowing which code to target comes with practice.

Test are typically broken into three stages : 
- Setup
  - At this stage, you will create some sample objects in your database that you can use to test your code.
  - Create a sample recipe that we can use to test our API Endpoint.
  '
  def test_partial_update_recipe(self):
    """Test updating a recipe with a patch"""
    recipe = sample_recipe(user=self.user)
    recipe.tags.add(sample_tag(user=self.user))
    new_tag= sample_tag(user=self.user,name='Curry')
  '
- Execution
  - This is where we actually call the code being tested.
  '
  def test_partial_update_recipe(self):
    """Test updating a recipe with a patch"""
    recipe = sample_recipe(user=self.user)
    recipe.tags.add(sample_tag(user=self.user))
    new_tag= sample_tag(user=self.user,name='Curry')
    
    payload = {'title':'Chicken tikka','tags':[new_tag.id]}
    url = detail_url(recipe.id)
    self.client.patch(url,payload)
  '
  
  - Assertion Stage:
    - At this stage, you check for the code performed, what it was supposed.
    - So, in the recipe example, we will ensure, that the appropriate fields, on our sample recipe were updated to correct value.
  '
  def test_partial_update_recipe(self):
    """Test updating a recipe with a patch"""
    recipe = sample_recipe(user=self.user)
    recipe.tags.add(sample_tag(user=self.user))
    new_tag= sample_tag(user=self.user,name='Curry')
    
    payload = {'title':'Chicken tikka','tags':[new_tag.id]}
    url = detail_url(recipe.id)
    self.client.patch(url,payload)
    
    recipe.refresh_from_db()
    self.assertEqual(recipe.title,payload['title'])
    tags = recipe.tags.all()
    self.assertEqual(len(tags),1)
    self.assetIn(new_tag,tags)
  '

-  Why write test cases?
  - It makes it a lot a easier to maintain and make changes.
  - When you make changes to the code which has code coverage, you are confident that if anything breaks, you will get to know when the test run.
  - This way you can fix the issue, before they arise in production build.
  - Adding features and making changes become a lot easier with the added confidence that tests bring. 
  - Another great benefit, it encourages the developers to write testable code. In order for code to be testable, there must a clear input and output for each unit of code. This makes it, easy to read reliable code.
  
  The classic way to write unit test is you write the piece of code and then you write the unit tests. 
  
  Implement Features -> Write Tests
  
  With TDD, all you have to do is switch this round.
  You start by writing unit test, then you ensure that test fails, then implement the code or feature to pass the test.
  
  What's the benefit of doing this way ?
  - Increases the test coverage.
  - You can ensure that all code  written with TDD has been tested. 
  - It ensure, that your test actually works. 
  - It also encourage us to write good quality code, naturally.
  - Lastly, the unit test serves as the guideline  for when to stop coding. This help us keep on track and focused. 

Happy Learning!

Rajiv Jha :)
