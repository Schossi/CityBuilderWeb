---
permalink: /manual/releases
title: "Release Notes"
sidebar:
  title: "Manual"
  nav: manual
---

## 1.6.1

### ADDED
- ZoomCollider on CameraController can keep camera from clipping  
(used in town demo and three demo stage two)

### FIXED
- TerrainModifier not replacing TerrainData in collider  
(caused bad highlighting in generated town demo scenes)

## 1.6.0

### ADDED

- TerrainRoadManager visualizes roads by changing terrain texture 
- Terrain option in Setup Dialog
- MovementPlayground and BuildingPlayground test scenes
- DepopulationHappening which kills a fraction of the population
- TownDemo
  - title screen, menus, difficulty, map generation
  - market building, distribution task, peddler job
  - road tool and task
  - views for food, wood and actions
  - test project
  - inspector tooltips, xml documentation
  - ...

### IMPROVED

- TerrainModifier can also save height and texture
- GridHeight is applied to Buildings
- Walker can use NavMeshAgent for movement
- BuildingBuilder adjusts position based on camera direction
- CameraController now saves rotation

### FIXED

- LayerKeyVisualizer on scaled canvas
- HasPoint on NavMesh when elevated

## 1.5.1

### ADDED

- PopulationVisualizer that displays population quantity and capacity
- ManualExpansion allows placement of ExpandableBuilding in Editor

### CHANGED

- DistributionComponent  
no longer discards items the seller brings back if the storage has been filled  
additional new option on SaleWalker to reserve space for the items it carries
- TownHomeComponent spawns walkers even when empty 

### FIXED

- ProductionWalkerComponent missing calls to base methods
- StructureTerrainTrees not changing on load
- TownDeliveryTask not finishing when items are brought directly
- TownGatheringComponent and TownForestingComponent task cleanup and saving
- TownFieldTask was missing walker assignment

## 1.5.0

first in a series of 2-3 updates that focus on the new CityBuilderTown demo, documentation and core framework improvements

### ADDED

- CityBuilderTown[EXPERIMENTAL]
  - terrain based
  - task system
- Walker Actions and Processes
  - higher level walker control
- Risk- and ServiceCategory
  - building and walker bars
  - service category evolution
- Building Prefab Alternatives
- ItemConstructionComponent
  - replaces building when items have been supplied

### IMPROVED

- Documentation
  - header comments for all core objects
  - descriptions for demo manual pages
  - core building components manual diagram
- Walker now directly exposes an Animator
  - animation parameters on WalkerInfo(Walk, Direction, Carry)
- additional storage modes(ItemSpecific, TotalItemCapped, TotalUnitCapped)
- various interfaces simplified

### FIXED

- mouse wrongly touch panning
- camera shake on middle mouse drag

## 1.4.6

### ADDED

- Mobile support for Urban and Defense Demos
  - adjusted UI
  - added touch controls
- WalkerAreaMask (NavMesh areas for use in PathTag)

## 1.4.5

### ADDED

- More uses for PathTag (see Walkers manual page)
  - RoadBlockers in Three Demo can be set to let certain Walkers pass
  - Different Pathing by Ground Tile in StructurePathDebugging test scene

### IMPROVED

- URP upgradability for Three demo (see CityBuilderThree/URP)
- Employment Priorities are displayed in descending order

### FIXED

- Service Values increasing over time instead of decreasing
- walker rotation in urban tunnel scene
- three props now use the correct materials 
- links in manual pdf

## 1.4.0

### ADDED

- Food View in Three Demo  
uses the overhauled views and bars and the new IItemHolder interface  
walkers can now also have bars; added bars that show items using their icons
- Tornado Happening in Urban Demo

### IMPROVED

- Health Bars in Defense Demo reintegrated with Core Views and Bars
- Rain in Three Demo now affects Heat and Water  
the new ILayerModifier interface can be used to globaly affect Layers
- Religion in Historic Demo now affects Farming Efficiency  
the new ScoreEfficiencyComponent uses a Score to affect Building efficiency
- Migration in Three Demo is now driven by a Score  
this happiness score combines employment, housing quality and food availability

### FIXED

- suppressed unused event warnings
- recursive error in retrievers
- missing sprites in urban demo
- minor errors in tests

## 1.3.0

### ADDED

- __Timings__ system (events, animations and text based on playtime)
- __Hexagon__ support in Setup, Map, Tiles, ...
- Decorator Structures that save rotations and sizes
- Object Generator for easy map object generation

### IMPROVED

- FireWalker in Three Demo now actively walks to and extinguishes fires
- Walkers use better points to enter and exit buildings(Pathfinding accepts multiple starts/ends)
- BuildingRequirement can now require Buildings(see BuildingRequirementDebugging)
- DefaultGameManager now saves the current randomization state

### FIXED

- AccessType Exclusive
- Rotations in XY Maps

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