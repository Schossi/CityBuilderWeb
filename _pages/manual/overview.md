---
permalink: /manual
title: "Overview"
sidebar:
  title: "Manual"
  nav: manual
---

## Welcome

This is the manual for Classic City Builder Kit by SoftLeitner. Classic City Builder Kit is quite the mouthful so I will be referring to it using the shorthand CCBK.  

Oldschool walker based City Builders are very systems heavy games that require lots of tweaking and balancing to get right. CCBK was created with the aim of providing all the common tropes of the genre and making them easily accessible in the Editor.  

The kit was created with the classic evolve housing, build monuments type of game in mind and most of the systems are commonly seen in that genre. That being said large parts like Buildings, Items, Walkers and Layers are general enough to create a wide variety of games.  

This manual includes overviews of the demos, how to pages and explanations for all the major systems. More detailed explanations of individual components, interfaces and methods can be found directly in the code of the asset as xml headers and comments. These are also found in the online API documentation reached by clicking the ? button on any CCBK component in the unity inspector. Quick descriptions of most scenes in the asset can be displayed by clicking the About button in the scene view.

## Project Structure

CCBK is separated into multiple assemblies. Which ones you need depends on how you are planning to use the Kit. For your first exploration create a new project and remove the example assets and materials, then import the entire asset. Importing project settings is optional except for TagManager if you want to run the demos. 

* CityBuilderCore  
The Core Framework of CCBK, always import this one.

* CityBuilderCore.Tests  
Contains various automated and manual testing scenes for CityBuilderCore.  
Can be useful to explore how various systems work and how they are set up.  

* CityBuilderDefense  
Contains the [2D Tower Defense]({% link _pages/demos/demoThree.md %}) demo  
Import if you want to start by adapting this demo.

* CityBuilderManual  
Holds completed samples of the HowTo section of this manual.  
Import if you're stuck on a how to or exploring.

* CityBuilderThree  
Contains the [3D City Builder]({% link _pages/demos/demoThree.md %}) demo  
Import if you want to start by adapting this demo.  
__For the menu to work add the Menu, StageOne, StageTwo, StageThree scenes in Build Settings.__

* CityBuilderTown  
Contains the [3D Colony Sim]({% link _pages/demos/demoTown.md %}) demo  
Import if you want to start by adapting this demo.  
__For the menu to work add the TownTitle and TownHills scenes in Build Settings.__

* CityBuilderTown.Tests  
Contains some automated and manual testing scenes related to the town demo.
Can be useful to explore how some of the specialized town demo systems work.  

* CityBuilderUrban  
Contains the [2D City Sim]({% link _pages/demos/demoUrban.md %}) demo  
Import if you want to start by adapting this demo.

Most demos depend on either layers, tags or sorting layers. __If these settings were not set during import please copy the contents of TagManager.txt from the demo folder to the TagManager.asset in you ProjectSettings.__  

### Dependencies
* The demos depend on [TextMeshPro](http://docs.unity3d.com/Packages/com.unity.textmeshpro@2.1/index.html) for their UI
* CCBK(even in 3D) generally depends on [2D Tilemap Editor](https://docs.unity3d.com/Packages/com.unity.2d.tilemap@1.0/manual/index.html)

## Usage

After familiarizing yourself with CCBK you should be ready to start your project. I'll outline three basic levels of usage for CCBK here. The first two don't require any coding, implementing custom systems assumes basic knowledge of C#.

* Adapting one of the Demos  
Is one of the demos close enough to what you are trying to achieve? Great!  
Import it along with CityBuilderCore and the Settings and start tweaking. The content of the demos is explained in detail in the [3D City Builder]({% link _pages/manual/demos/three.md %}) and [2D Tower Defense]({% link _pages/manual/demos/defense.md %}) manual pages. 

* Starting from Scratch using Core Logic  
If none of the demos gets close enough to what you want to make or you want to make sure you understand every piece of your project starting from scratch is the way to go. [Continue Here]({% link _pages/manual/howto/two.md %}) for a step to step guide to creating a city builder purely in Unity Editor.

* Implementing Custom Logic  
Need some special sauce in your game and know basic C#. [Continue Here]({% link _pages/manual/howto/custom.md %}) for a step to step guide to extending CCBK with your own components and systems.

## URP

If your project does __not use URP__ please make sure the URP __package is not installed__. Some shaders like ThreeMapRoad and HeightMapped render differently when the package is present. Having the URP package but using Built-In can lead to wrong visuals.

The demos use the built in renderer to provide maximum compatibility. Most of the materials use default built in shaders which can be automatically upgraded using the URP Material Converter.  

The THREE demo uses some custom shader for its terrain which can be recreated in URP using certain settings in the renderer. These settings are included in the asset. They can be found in the CityBuilderThree/URP folder along with some instructions on how to upgrade to URP.

## Input

CCBK uses the built in input system. It is recommended to remove the new input system package if it was added from one of the newer templates in unity 6.

## Navigation

The newer NavMesh components are not currently used in CCBK. It still uses the global NavMesh workflow(baking navmesh from Navigation Tab) to maintain backwards compatibility to older Unity Versions. The difference between the two is not that big though and depending on the use case it can be changed relatively simply.

For example to switch the Debug scene in the __Three__ demo we would do the following.
- Delete the existing baked NavMesh in the Debug subfolder
- Activate the 'Navigation' gameobject which contains the baking objects
- On the red cube that blocks walking on the river create a NavMeshModifierVolume
  - Set AreaType to 'NotWalkable' and adjust the Size
- Create a NavMeshSurface component on 'Navigation'
  - Set CollectionObjects to 'CurrentObjectHierarchy'
  - Click the 'Bake' button to bake a new NavMesh
- Deactivate the gameobjects below 'Navigation'
- Click 'Play' and build a Property to check that navigation works correctly

The 'CurrentObjectHierarchy' may not be applicable in all scenarios. When this is the case you may want to separate out different objects by layer and change the IncludeLayers setting. In the __Town__ demo no changes may need to be made whatsoever as the NavMesh is not baked upfront in that demo but instead by the NavMeshUpdater component.

## Roadmap

Current development is focused on three main areas:

* polishing the demos
* extending and refining core
* improving documentation

## Feedback

The quickest channels to reach me are mail and discord. Please feel free to reach out with any problems and questions. Feedback regarding the general direction of CCBK and particular future features are also always welcome. Though I might not immediately be able to incorporate your requests I very much take them into consideration when planning out future updates.  

If you can spare the time please consider leaving a review in the asset store.