---
permalink: /manual/releases
title: "Release Notes"
sidebar:
  title: "Manual"
  nav: manual
---

## 1.8.7

### ADDED
- MoveTool  
allows moving and rotating one or more buildings and structures  
IsMovable field added to BuildingInfo and different structure components  
tool added in sidebar in various scenes, move button added to three building dialog
- ConnectionPlayground(CityBuilderCore.Tests/Other)  
playground scene that allows trying out Connection system on its own  
also check out the new Connections manual page which explains connection fundamentals
- ConnectionFeederBuilder  
special building builder that shows preview of connection  
used in playground and urban demo power station
- LayerPlayground(CityBuilderCore.Tests/Other)  
playground scene that allows trying out Layer system on its own  
- LayerBuildingBuilder  
special building builder that previews layer values by highlighting or tilemap  
used in playground(LayerPreview tilemap) and on three demo gardens(highlighting)
- SelectionSwitcher  
allows switching through buildings and walkers of the same type from dialogs  
using in three and town demos(special variant in town demo that switches by job)

### IMPROVED
- HelpUrl  
clicking the ? button on an AAK behaviour will now open the API documentation
- ConnectionPasserStructure now allows specifying structure by Key  
this allows passing connections through roads as shown in the connection playground
- ViewLayer now also visualizes points with 0 value if they are affected by something  
avoids strange looking gaps in the overlay when layer value adds up to 0 between affectors

### CHANGED
- tool cancellation no longer bound to framerate
- selection tool needs full click instead of just mouse up
- DefaultStructureManager subscribes to PointsChanged for every type of structure
- CheckBuildingRequirements renamed to CheckRequirements  
and split into CheckBuildingRequirements and CheckRoadRequirements

### FIXED
- height calculation for ghosts different from placed buildings
- urban power lines did not refresh connections on destroy

## 1.8.6

### IMPROVED
- default highlight manager can highlight tiles with colors(mouse over highlights)
- meta save data is deleted with the regular save data 
- rotating the camera with RMB does not cancel tools(click held longer than 0.1s)
- highlights and layer keys are not shown when mouse is outside map
- building and walker addon queue is now also persisted
- canceling of roaming and walking  
cancellation is stored in walking state leaving walking path mostly stateless and reusable
walking by method or process and cancelling can be tested in MovementPlaygroundGrid
- additional xml documentation in code

### FIXED
- copy and deleted buttons in editor dialogs too small in newer unity versions
- bug when saving the game in town demo before placing the initial building

## 1.8.5

### ADDED
- WalkerAddons  
reusable piece of logic that can be added to walkers very similarly to BuildingAddons  
BuildingAddon has also received some improvements to keep in line with this addition
  - Save field that sets whether an addon is persisted and recreated on load
  - Accumulation field sets what happens when an addon is added more than once
  - Walker/BuildingAddonHappening that adds addons when active(epidemic in three)
- Slower building in the defense demo  
applies slow addon to attackers which slows them and shows a blue capsule

### IMPROVED
- SelectionTool visualizes hovered point, walker or building in town and three demos  
highlighting used to visualize points, walkers and buildings by using addons
- SelectionDialog and town dialogs visualize selected walkers and buildings
- CameraController can pan, zoom, rotate and pitch on both mouse buttons  
MiddleMouseButton:  default>pan shift>rotate&pitch alt>zoom  
RightMouseButton:   default>rotate&pitch shift>zoom alt>pan
- ItemStore can be persisted by one of the connected storages  
see StorageDebugging for an example of two storages using the same ItemStore
- additional test for town demo that tests home provisioning
- switch between walkers and their home in town dialogs
- stacked storages can reserve capacity
- additional custom editors
  - trigger timing happenings(epidemic, rain, ...)
  - town walker editor
  - storages show reservations

### FIXED
- task cancellation on walker death in town demo
- ItemStorage MoveItemsTo correctly returns the moved quantity 
- town demo building dialog error in empty homes

## 1.8.4

### ADDED
- Sounds  
Town demo now has UI sounds, an atmospheric background track and various sounds for tasks like harvesting stone or chopping wood
  - AudioPool to play sounds like button clicks from a central component
  - AudioSlider that sets and persists volume levels
- MissionSelector  
example scene that demonstrates an alternate setup for a menu screen(CityBuilderCore.Tests/Other/MissionSelector)
- TaskList  
used in the Three demo for a multi stage tutorial
- MessageBox  
generic message box dialog(Ok, OkCancel, YesNo, YesNoCancel)
- Messaging  
allows sending messages and attaching events to buildings and walkers  
Town uses this to send messages from animations to the current task where it plays a sound

### CHANGED
- DefaultMap no longer clamps points, clamping is done in CameraController instead

### FIXED
- tooltips sometimes not exiting

## 1.8.3

### IMPROVED
- continue game from last saved data  
new buttons using this functionality in Three and Town demos
- whether a stage is finished is saved per stage and per save game  
this allows beating the stage again on a new save

### FIXED
- walkers using navmesh agents cancelling on load
- exception in storage component with older data

## 1.8.2

### IMPROVED
- ItemStorage has new ItemStorageMode called Store  
allows redirecting to a seperate ItemStore component  
for example to combine storages across a building
- TerrainMap now derives from DefaultMap  
this enables blocking through tilemaps on TerrainMap 
- various custom property drawers  
ItemQuantity, ItemStorage, BuildingRequirement, ...
- storage orders are now also persisted

### FIXED
- GetItemQuantity on MultiItemContainer leading to wrong display in UI Panel
- service category recipient not triggering evolution

## 1.8.1

### ADDED
- additional debug options in the inspector in play mode  
for example items can be added directly to StorageComponents  
available for Building and various BuildingComponents

### FIXED
- DeliveryWalker looking for storages in Load before storages are full loaded
- GridPathing allowed invalid paths by default, now behind const ALLOW_INVALID
- ServiceCategory was not fully integrated in Evolution
- Invalid tool selection in new game in TownDemo after placing startup
- TMPro warning in TownDemo due to unnecessary CanvasRenderer
- Validation that prevents global storage from being configured to access itself 

## 1.8.0

minimum recommended unity version has been raised to 2021.3.29

### ADDED
- minimal demo scene demonstrating simple placement  
CityBuilderCore.Tests/Other/Placement/Placement.unity
- Buildings can now be suspended and resumed  
temporarily stops them from working without having to demolish and rebuild them  
(see checkmarks Three and Town demos building dialogs) 
- simple SavingIndicator in all demos
- simple spawn(BuildingAddonSpawn) and despawn(DemolishVisualDespawn) animations  
(see Placement demo)

### IMPROVED
- Migrations can be configured to use multiple entry points  
(see PlebMigration in Three demo Debug scene)
- Box option in StructureBuilder to build in a rectangular shape  
(see RugTool in Placement demo)
- Override option in StructureBuilder to remove other structures  
(see RugTool in Placement demo)
- Demolish tool has new LevelsNext field to configure order of deletion
(see DemolishTool in Placement demo) 

### FIXED
- tooltip position in scaled canvas
- various minor adjustments to accommodate higher unity version

## 1.7.4

this will be the last version based on unity 2019.4.18, the next update will increase the minimum version to a more recent LTS

### ADDED
- tagged requirements on DefaultMap and TerrainMap  
define certain building restrictions on the map by tag(building, road, structure)  
check out BuildingPlaygroundTagged and BuildingPlaygroundTerrain for some examples

### IMPROVED
- StructureBuilder can now be used for any structure

### FIXED
- removal of old roads on load
- harvesting of grown trees in town demo
- gaps in terrain road visuals in some maps

## 1.7.3

### ADDED
- Off Grid Link  
equivalent to OffMeshLink in NavMesh but for grid(road) walking  
see debug scenes LinkRoadDebugging and BuildingPlaygroundLink
- Mesh Highlight Manager  
visualizes highlights by modifying meshes during runtime  
used in town demo to dramatically improve highlighting performance  
three demo uses mesh highlighting with nice rounded outlines  
see BuildingPlayground2D for simple pixelated outline
- Variant Production Component  
more versatile production component that allows configuring different variants  
see ProductionDebugging test scene for some examples

### IMPROVED
- better handling of mouse position outside play area
- town demo harvest tool performance dramatically improved

## 1.7.2

### ADDED
- Tooltips
- Walker and Building Dialogs in Town Demo
- Notifications in Three Demo(Risks, Monuments)

### CHANGED
- Building Alternative is rotated on build

### FIXED
- Error in Editor Windows with Unity 2021
- TownConstruction finishing prematurely
- Error caused by Harvest Tasks being restarted
- Off Mesh Link on Bridges in Three Demo

## 1.7.1

### ADDED
- Notification System and Notifications for
  - Town Constructions finishing
  - Town Season changing
  - Town Walkers dying
  - Urban Tornados
- Town Trees falling down is now visualized
- Town Walkers can visualize Tools for Tasks
  - Woodcutters and Foresters use an Axe

### FIXED
- critical bug preventing loading of most walkers
- bridges not working as roads after reloading
- worker walkers bug when site loads later or is destroyed
- dead town inhabitants not being removed from their home
- some other minor fixes in the town demo

## 1.7.0

### 3D Colony Sim Demo

This release marks the official promotion of [CityBuilderTown]({% link _pages/demos/demoTown.md %}) from experimental to an official demo. This means a removal of all placeholders and a rework of all elements of the demo. This includes a completely __new Set of Low Poly 3D Models__ used in that demo.

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