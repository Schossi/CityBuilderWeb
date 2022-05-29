---
permalink: /manual/urban
title: "2D City Sim"
sidebar:
  title: "Manual"
  nav: manual
---

Art assets have been adapted from sprites made by opengameart user [pixel32](https://opengameart.org/users/pixel32)

Play it [here]({% link _pages/demos/demoUrban.md %}).  

Demonstrated Connections, Multi-Road-Networks and Multi-Level-Structures. Which level each of the structures occupies is shown in the last column(Underground-Road-Building >> XXX, OXX, ...). The other building components and walkers in this demo are mostly custom made for the urban demo and not part of the core components.

## Buildings

|![Railstation](/assets/images/urban/railstation.png)|__Railstation__|RailwayComponent|Goods|OXX|
|![House](/assets/images/urban/house.png)|__House__|ConnectionPasserComponent<br/>LayerEfficiencyComponent<br/>HouseComponent|Power<br/>Water<br/>Van|OXX|
|![Shop](/assets/images/urban/shop.png)|__Shop__|ConnectionPasserComponent<br/>LayerEfficiencyComponent<br/>ShopComponent|Power<br/>Water<br/>Money|OXX|
|![WaterPump](/assets/images/urban/pump.png)|__Water Pump__|ConnectionPasserComponent<br/>ConnectionFeederComponent<br/>LayerEfficiencyComponent|Power<br/>Water<br/>Water|XXX|
|![PowerStation](/assets/images/urban/powerstation.png)|__Power Station__|ConnectionFeederComponent|Power|OXX|

The Railstation building manages train and truck walkers. It periodically spawns a train walker. When a train arrives it spawns a truck.

Houses have two components that influence their efficiency. The ConnectionPasserComponent needs an UrbanPowerSupply to pass through it and the LayerEfficiencyComponent checks the UrbanWater Layer.  The resulting efficiency influences both the TimedReplacementComponent which upgrades a house after a set time and the HouseComponent which sends out UrbanVan walkers which purchase goods from any shops they pass. The sprite a house uses is randomly chosen and persisted by the SpriteRandomizerComponent, it even passes the chosen sprite along to the next house when it upgrades.

Shop also need Power and Water to work just like houses. When they are passed by a vans that are sent out by houses the van receives some of the goods in the shop. This makes space for new goods that are delivered by the trucks that the Railstation sends out. When shops replenish their stock from trucks a certain amount of money is also generated and added to the global storage that is used to build new buildings and infrastructure.

The WaterPump needs power and water too. When it has these it feeds into the UrbanWaterSupply Connection which is passed on in pipes. Unlike the other buildings it also occupies the lowest structure level which can be controlled in the Level field of the UrbanWaterPump BuildingInfo. It also has a gameobject called pipe that lies on the Water Layer and will therefore only be visible when a view that show that layer(UrbanWaterCulling) is active. 

One behaviour all the buildings that connect to the power grid have in common is the StructureTileRefresher. This script simply refreshes all the nearby tiles of the powergrid so the correct tile that connects to the building is chosen.

Lastly there is the PowerStation building which simply feeds into the UrbanPowerSupply Connection that is passed on by power lines. 

## Structures

|![PowerLines](/assets/images/urban/powerLine.png)|__Power Lines__|StructureTiles<br/>ConnectionPasser|POW<br/>Power|OOX|
|![Pipes](/assets/images/urban/pipe.png)|__Pipes__|StructureTiles<br/>ConnectionPasser|PIP<br/>Water|XOO|

PowerLines pass on the UrbanPowerSupply Connection. They only occupy the upper structure level in which makes it possible to build them on top of roads which only occupy the middle one.

Pipes pass the UrbanWaterSupplyConnection, if you check the Connection in the assets you can also find that it influences the UrbanWater Layer for a range of 5 and with a falloff of 1. 

As you can see in the respective gameobjects(Grid/Water, Grid/Power) both of these structures combine a StructureTiles behaviour with a ConnectionPasserStructure which takes the points of the structure and adds it into the connection system. They also have a ConnectionTileGradient that visualizes the amount of connection at every point of the structure by tinting the tile with a gradient.

## Walkers

|![Train](/assets/images/urban/train.png)|__Train__|TrainWalker|Rail|
|![Truck](/assets/images/urban/truck.png)|__Train__|TruckWalker|Road<br/>100 Goods|
|![Van](/assets/images/urban/van.png)|__Train__|VanWalker|Road<br/>5 Goods|
