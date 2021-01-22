---
permalink: /manual/structures
title: "Structures"
sidebar:
  title: "Manual"
  nav: manual
---

A structure is basically anything that is placed on the map.  
The default structure manager stores basic structures in a dictionary based on the position, so checking and retrieving structures when the position is known is fast. This has the downside that only one regular structure can be stored per position. Since only Buildings are stored this way in Core CCBK this is not a problem.  
StructureCollections and Tiles are always stored seperately and Roads register themselfes as underlying structures which also stored them in a seperate list.

Structures are defined by the points they occupy on the map as well as three bit flags:
* IsDestructible  
Specifies whether the structure can be removed by the player
* IsDecorator  
Decorator structures are automatically removed when something is built on top of them
* IsWalkable  
Whether the MapGrid Pathing Type includes the points of the structure 

## Roads

The DefaultRoadManager is a special structure that includes all the points that are filled out in the TileMap on the GameObject and does pathfinding between them.
It is possible to define multiple Roads with different Stages that work similar to Building Evolutions.
> simple paths turn into prettier streets when the desirability of the area improves  

## StructureCollections

A collection of GameObjects that interact with the map somehow.  
Only one kind of GameObject is allowed per collection and the prefab has to be specified. This is done so the Structures can be restored after the game is loaded.

> 3D - trees, rocks, rubble, walls...

## StructureTiles

Similar to StructureCollections but using Tiles instead of GameObjects.

> 2D - trees, rocks, rubble, walls...

## Buildings

see [Buildings]({% link _pages/manual/general/buildings.md %})