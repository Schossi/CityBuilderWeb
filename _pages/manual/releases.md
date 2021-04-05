---
permalink: /manual/releases
title: "Release Notes"
sidebar:
  title: "Manual"
  nav: manual
---

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

### CHANGED

- demo materials have been switched from urp to legacy shaders  
- sort axis moved to camera controller

### FIXED

- blockers not working after save/load
- building walkers not triggering on spawn
- panning in xy isometric maps
- speed controls in historic demo

## 0.9.0

__Initial Release__