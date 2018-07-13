---
layout: post
title: Inner Product Space - Part I
date: 2018-07-13 02:32:20 +0530
description: Princple component Analysis - Basic concept
img: vector.png
tags: [Hackathon]
author: Rajiv Jha
---
July 13, 2018

Hello!
Inner products are the generalized form of dot products and is useful in dimesnsion reduction in principal component analysis, which is a major field of Machine learning & Data science.

# Basics of Inner Products 

Inner product, V is the function on cross product.

`Let, V = (C ^ n) : an inner product, where C is the complex vector space`

`on V is a function < . , . > : V * V -> C`

which satisfies the following condition.

- <x,x> must be non-negative real number , where x belong to V : Positive definiteness of Inner product
- <x+y,z> = <x,z> + <y,z> for x,y,z in V : Linearity with respect to first argument/variable (Bilinear)
- <Mx,y> = M<x,y> , true for all M in C : Linearity with respect to first argument/variable (Bilinear)
- <y,x> is the complex conjugate of the image of <x,y> : Conjugate symmetry

A vector space, V together with an inner product < . , . > is called an inner product space (V , <.,.>).


> To learn more about Inner products, Stay Tuned.

Hope this helps!
Keep tuned for more blogs from ML series.

Happy Learning!

Rajiv Jha :)
