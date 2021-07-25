---
permalink: /manual/releases
title: "Release Notes"
sidebar:
  title: "Manual"
  nav: manual
---

## 1.2.0

### ADDED

- __Overview Windows__ for Buildings, Walkers and Items  
these display all the objects in a set with preview images  
objects can be filtered, cloned and deleted 

### IMPROVED

- __Complete visual overhaul of 3D City Builder Demo__  
  - __25 Original Low Poly Buildings__
  - Humanoid Walkers with Animations
  - Maps, Props, Materials, Effects, ...
- Updated "Start from Scratch" Tutorial
  - Incorporates new Setup and Overview Windows
  - New sprites for Buildings and Walkers

### CHANGED

- Common walker properties have been moved to WalkerInfo  
PathTyp, PathTag, Speed, MaxWait, Delay

### FIXED

- Expandable buildings not loading their expansion
- Buildings having wrong scale after being affected by BuildingAddonTransformer  
this lead to buildings in the three demo always being slightly off scale or very off scale when the framerate was low
- Roads for Bridge being amended without rotation
- Path Recalculation for moving walkers in Defense Demo
- Roads being demolished when their RoadBlocker was demolished  
Roads are "underlying" and therefore only demolished when no non "underlying" structure is demolished at the same time
- Pooled walkers retaining their items and state
- ...

## 1.1.0

### ADDED

- __Setup Wizard__ window  
creates a clean project template with placeable buildings  
configure display modes, axis, sizes, ... in a simple dialog
- __Expandable Buildings__  
building size is determined during building  
expand building in one or two dimensions  
showcased in the new bridge building of THREE demo
- enhanced __Full 3D__ support  
showcased in new 3D demo scene in THREE demo  
support for perspective camera and 3D roads  
height parameter in walkers can modify their display  
(move along terrain or change to different layer in tunnel) 
- __Road Switching__  
allows destination walkers to move between road networks  
showcased in SwitchRoadDebugging scene in tests and tunnel scene in urban demo   

### IMPROVED

- __Building Requirements__ now support various modes and configurations  
- __Road Requirements__ can now be configured to amend missing roads  
- __Cell Size__ of grid is taken into account in default and isometric map

### CHANGED

- RoadBuilding functionality has been merged into regular Buildings

### FIXED

- incorrect camera area when camera was pitched enough to look up
- structure level editor not working inside arrays
- monument pathing when using worker pooling
- ...

## 1.0.0

### ADDED

- __urban demo project__  
simple city sim in isometric 2d  
showcases various 1.0 features
- __connections__ core system  
build a network of feeders and passers  
enables water and electricity networks
- __connected tiles__ that switch sprite based on their neighbors  
simple base class and variants for rectangle and isometric grids

### IMPROVED

- __walkers__ can now be pooled using ObjectPool  
- __roads__ now support multiple networks  
simply use MultiRoadManager instead of DefaultRoadManager  
> rails and roads in urban demo
- __structures__ now support multiple levels  
easily control which levels a structure inhabits using the level toggles
> a single point in the urban demo can have a pipe, road and power line; pumps inhabit all three levels  
- new __view__ type that displays building efficiency

### CHANGED

- demo materials have been switched from urp to legacy shaders  
- sort axis moved to camera controller

### FIXED

- blockers not working after save/load
- building walkers not triggering on spawn
- panning in xy isometric maps
- speed controls in historic demo
- ...

## 0.9.0

__Initial Release__