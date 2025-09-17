---
title: Midterm-Guidelines
draft: false
description: description
---

## Summary

Using the principles of Object Oriented Programming, create a lively scene filled with spontaneous interactions and procedurally generated entities.

[Doug's Train Scene Example](https://dougrosman.github.io/creative-code-projects-fa25/midterm/)
## Guidelines

Your scene should contain the following:
1. "**Objects**" with...
	1. **traits** that are generated randomly (or pseudo-randomly) based on pre-determined rules. Think of these like traits (the speed of a car, the color of a bird, etc.)
	2. **behaviors** that make the objects change their state (e.g. a car changes position based on its speed)
	3. **interactions** where objects change their state or behavior depending on the state or behavior of another object (e.g. if my object is near another object, if my object is bigger than another object)
	4. **events**, determined by the web context (e.g., what happens when the page loads? What happens when the page is resized? What happens if a user clicks?)
2. An "**environment**" where the objects interact. Some trait or behavior of your objects should depend on some aspect of the environment. (e.g. the trains are positioned on the track)

Your scene should run autonomously and potentially forever, meaning that once it starts running, it should be able to continue running on its own.

## How to approach this assignment

1. **Imagine your scene** and write a brief summary of it. Your summary doesn't have to be detailed, just give a broad overview of the basic environment, objects, behaviors and interactions.
2. **Expand your summary**: create a diagram or outline of the elements of your scene, being as specific as possible. Note: The diagram below is an example, you can create your diagram on pen and paper, or with the software of your choice.
3. **Start your code:** Work on it from the bottom up. First, work on the smallest element of your scene (e.g., a single train car). Then, work on parent element (e.g. an entire train car). If you don't have any parent elements, that's okay!


![[train-scene-diagram.png]]

