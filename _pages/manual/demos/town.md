---
permalink: /manual/town
title: "3D Colony Sim"
sidebar:
  title: "Manual"
  nav: manual
---

!!! EXPERIMENTAL !!!!!! EXPERIMENTAL !!!!!! EXPERIMENTAL !!!

Open TownTitle to try the game out the same way a player would(TownTitle and TownHills have to be added to Build). To quickly jump in you can use TownDebug or TownDebugFilled which has a bit more stuff set up. The debug scenes also have a debug tool bar above the normal one that lets you build and demolish things instantly.

If you are interested in some of the individual systems of the town demo you can also check out the CityBuilderTown.Tests project which contains various test scenes. Some of them can also be quickly run through with the test runner to confirm that the systems still work after modifications.

### Buildings

- __House__ lets occupants eat and warm up and produces new walkers
- __Barn__ stored food
- __Gatherer__ creates tasks for gathering berries
- __Farm__ creates tasks for working fields
- __Forester__ creates tasks for planting and cutting down trees
- __Woodcutter__ creates tasks for turning logs into wood needed to warm up
- __Market__ distributes wood and food to houses that are connected via roads

### Tools

- __Harvest__ creates harvest tasks for trees, rocks and berries
- __Demolish__ removes tasks, creates demolish tasks for buildings

### Jobs

Jobs can be assigned to walkers from the UI on the bottom left. Tasks without a job, like clearing the ground or picking up items, can be done by any walker. Those with an assigned job will look for tasks that correlate to their job first though. 

- __Builder__ builds buildings when the ground has been cleared and needed logs and rocks have been delivered
- __Gatherer__ gathers berries
- __Farmer__ works farm fields
- __Forester__ cuts and plants trees
- __Woodcutter__ turns logs into wood
- __Peddler__ delivers items to the market and distributes them along roads

### Tasks

The Task system is the central defining feature of the Town demo. There is only one walker type which has a couple built in processes like getting food or idling. Every other action the walkers take is wrapped in a task that is located on a gameobject somewhere in the world. When they are not occupied by any of their needs walkers query the TownManager for an appropriate task. 

To create a new task with your own logic you can create a new script that derives from TownTask. A fairly simple task to check out before jumping into your own would be the TownItemTask. Some tasks may have state that needs to be persisted, for an example of that check out TownBuildTask.

Tasks as well as the walkers heavily rely on the new walker actions and processes. To learn more about them check out the [manual section]({% link _pages/manual/general/walkers.md %}#walkeraction) and the xml documentation in their code.

|__Build__ |progresses the construction it belongs to|Builder|
|__ClearGround__ |clears the ground before construction takes place|-|
|__Collect(Item)__ |different items waiting to be picked up and stored|-|
|__Deliver__ |gets walkers to supply its receiver(Construction, Production, Market) with items|-|
|__Demolish__ |removes the building/road it is on|-|
|__Distribute__ |makes the walker roam and distribute food and wood on roads connected to the market|Peddler|
|__Field__ |gets tilled in spring, grows on its own in summer and harvested in autumn|Farmer|
|__GatherBerries__ |gets berries from bushes without destroying them, empty bushes regrow|Gatherer|
|__HarvestBerries__ |turns bush structure into berries item, periodically created by gatherer building|-|
|__HarvestRock__ |turns rock structure into stone item|-|
|__HarvestTree__ |turns tree structure into log item|-|
|__HarvestTreeF__ |turns tree structure into log item, periodically created by forester building|Forester|
|__Path__ |adds point it is located on to roads|-|
|__PlantTree__ |adds small tree that grows into full tree over time|Forester|
|__Work__ |building efficiency and therefore production rate depends on walkers performing this task|Woodcutter/...|

### Items

- __Stone__ for building
- __Log__ for building and producing wood
- __Wood__ for warming up in houses, limited in the UI bottom right to make sure there are logs left for construction
- __Potato__ for eating in houses
- __Berry__ for eating in houses


!!! EXPERIMENTAL !!!!!! EXPERIMENTAL !!!!!! EXPERIMENTAL !!!