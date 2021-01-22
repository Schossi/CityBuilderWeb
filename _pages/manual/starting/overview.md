---
permalink: /manual
title: "Overview"
sidebar:
  title: "Manual"
  nav: manual
---

## Welcome

This is the manual for Classic City Builder Kit by Softleitner. Classic City Builder Kit is quite the mouthfull so i will be refering to it using the shorthand CCBK.  

Oldschool walker based City Builders are very systems heavy games that require lots of tweaking and balancing to get right.  
CCBK was created with the aim of providing all the common tropes of the genre and making them easily accessible in the Editor through heavy use of Scriptable Objects.  

The kit was created with the classic evolve housing, build monuments type of game in mind and most of the systems are commonly seen in that genre. That being said large parts like Buildings, Items, Walkers and Layers are general enough to create a wide variety of games.  

## Project Structure

CCBK is seperated into multiple assemblies. Which ones you need depends on how you are planning to use the Kit. For your first exploration just import the entire asset into a new urp project.

* CityBuilderCore  
The Core Framework of CCBK.  
Always import this one.

* CityBuilderCore.Tests  
Tests some core functionality of CityBuilderCore.  
Only import this if you plan to change CityBuilderCore and want to check if the basic systems still function.  

* CityBuilderThree  
contains the [3D City Builder]({% link _pages/demos/demoThree.md %}) demo  
Import if you want to start by adapting this demo.

* CityBuilderDefense  
contains the [2D Tower Defense]({% link _pages/demos/demoThree.md %}) demo  
Import if you want to start by adapting this demo.

* Settings  
The different Unity Settings have to be imported if one of the demos is imported. This is primarily because of the Layers used. TODO CHECK 2D and Tests

## Usage

After familiarising yourself with CCBK there are basically three levels of usage. The first two don't require any coding, implementing custom systems assumes basic knowledge of C#.

* Adapting one of the Demos  
Is one of the demos close enough to what you are trying to achieve? Great!  
Import it along with CityBuilderCore and the Settings and start tweaking. The content of the demos is explained in detail in the [3D City Builder]({% link _pages/manual/demos/three.md %}) and [2D Tower Defense]({% link _pages/manual/demos/defense.md %}) manual pages. 

* Starting from Scratch using Core Logic  
If none of the demos gets close enough to what you want to make or you want to make sure you understand every piece of your project starting from scratch is the way to go. [Continue Here]({% link _pages/manual/howto/scratch.md %}) for a step to step guide to creating a city builder purely in Unity Editor.

* Implementing Custom Logic  
Need some special sauce in your game and know basic C#. [Continue Here]({% link _pages/manual/howto/custom.md %}) for a step to step guide to extending CCBK with your own components and systems.