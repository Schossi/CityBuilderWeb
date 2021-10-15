---
permalink: /manual/three
title: "3D City Builder"
sidebar:
  title: "Manual"
  nav: manual
---

Play it [here]({% link _pages/demos/demoThree.md %}), uses pretty much every system in CCBK except attacks.

<sub>While the visuals are now fully 3D this demo still uses Tilemaps for its logic. This means the [2D Tilemap Editor](https://docs.unity3d.com/Packages/com.unity.2d.tilemap@1.0/manual/index.html) is still required. For example the type of ground is still determined by the ground Tilemap, it is just invisible because its renderer has been disabled. So to block building or set layer values based on ground you need to enable the renderer, draw your changes and then disable it again.</sub>

## Buildings

### Housing

|![Property](/assets/images/three/buildings/property.png) |__Property__ |HousingPlaceholderComponent|Prefab: Tent|
|![Tent](/assets/images/three/buildings/tent.png)         |__Tent__     |HousingComponent<br/>EvolutionComponent<br/>RiskerComponent|Capacity: 5 Plebs<br/>Evolution: Housing<br/>Collapse: 1/s Disease: 3/s|
|![Hut](/assets/images/three/buildings/hut.png)           |__Hut__      |HousingComponent<br/>EvolutionComponent<br/>RiskerComponent|Capacity: 10 Plebs<br/>Evolution: Housing<br/>Collapse: 3/s|
|![House](/assets/images/three/buildings/house.png)       |__House__    |HousingComponent<br/>EvolutionComponent<br/>RiskerComponent|Capacity: 15 Plebs<br/>Evolution: Housing<br/>Collapse: 3/s|
|![Villa](/assets/images/three/buildings/villa.png)       |__Villa__    |HousingComponent<br/>EvolutionComponent<br/>RiskerComponent<br/>GenerationComponent|Capacity: 15 Plebs<br/>Evolution: Housing<br/>Collapse: 3/s<br/>Interval: 10 Items: 20 Gold|

### Risks&Services

|![Well](/assets/images/three/buildings/well.png)               |__Well__         |EmploymentComponent<br/>ServiceWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: WaterWalker|
|![Workshop](/assets/images/three/buildings/workshop.png)       |__Workshop__     |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: CollapseWalker|
|![Firefighter](/assets/images/three/buildings/firefighter.png) |__Firefighter__  |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: FireWalker|
|![Doctor](/assets/images/three/buildings/doctor.png)           |__Doctor__       |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: DiseaseWalker|
|![Treasurer](/assets/images/three/buildings/treasurer.png)     |__Treasurer__    |EmploymentComponent<br/>CollectionComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: TreasureWalker Storage: Global|

### Food

|![Farm](/assets/images/three/buildings/farm.png)     |__Farm__   |EmploymentComponent<br/>ProductionComponent<br/>LayerEfficiencyComponent|Group: Food Needed: 15 Plebs<br/>Interval: 10 Produces: 100 Potatoes<br/>Layer: Water Min: 0.2 Max: 100|
|![Hunter](/assets/images/three/buildings/hunter.png) |__Hunter__ |EmploymentComponent<br/>ItemsRetrieverComponent|Group: Food Needed: 10 Plebs<br/>Retriever: HunterWalker Downtime: 10|
|![Silo](/assets/images/three/buildings/silo.png)     |__Silo__   |EmploymentComponent<br/>StorageComponent|Group: Logistics Needed: 10 Plebs<br/>Storage: Stacked StackCount: 6 Capacity: 4 <br/>Orders: Accept Potato, Meat|
|![Market](/assets/images/three/buildings/market.png) |__Market__ |EmploymentComponent<br/>DistributionComponent|Group: Services Needed: 10 Plebs<br/>Storage: Unit Capped Capacity: 5 MinimumOrder: 1 Orders: Fill Potato, Meat|

### Production

|![IronMine](/assets/images/three/buildings/ironMine.png)       |__Iron Mine__    |EmploymentComponent<br/>ProductionComponent|Group: Production Needed: 10 Plebs<br/>Interval: 20 Produces: 1 Iron|
|![GraniteMine](/assets/images/three/buildings/graniteMine.png) |__Granite Mine__ |EmploymentComponent<br/>ProductionComponent|Group: Production Needed: 10 Plebs<br/>Interval: 20 Produces: 1 Granite|
|![Smith](/assets/images/three/buildings/smith.png)             |__Smith__        |EmploymentComponent<br/>ProductionComponent|Group: Production Needed: 10 Plebs<br/>Interval: 10 Consumes: 1 Iron Produces: 10 Tools|
|![Yard](/assets/images/three/buildings/yard.png)               |__Yard__         |EmploymentComponent<br/>StorageComponent|Group: Logistics Needed: 10 Plebs<br/>Storage: Stacked StackCount: 8 Capacity: 4 <br/>Orders: Accept Iron, Tools, Granite Refuse Potato, Meat|

### Workers

|![LabourCamp](/assets/images/three/buildings/labourCamp.png)           |__Labour Camp__      |CyclicWorkerProviderComponent<br/>ItemEfficiencyComponent|Prefab: LabourWalker Downtime: 5<br/>Item: Tools Interval: 10|
|![MasonCamp](/assets/images/three/buildings/masonCamp.png)             |__Mason Camp__       |PooledWorkerProvider|Prefab: MasonWalker Count: 2 Downtime: 3|
|![EntertainerCamp](/assets/images/three/buildings/entertainerCamp.png) |__Entertainer Camp__ |CyclicWorkerProviderComponent<br/>RiskerComponent<br/>LayerAffector|Prefab: EntertainerWalker<br/>Risk: Fire Increase: 5/s<br/>Layer: Desirability Value: -10 Range: 3 Falloff: -3|

### Other

|![ObelisksSite](/assets/images/three/buildings/obelisksSite.png) |__Obelisks Site__  |MonumentSiteComponent|Stages: CirclyPits, CenterPit, CircleObelisk, CenterObelisk<br/>various steps with different workers per stage|
|![Obelisks](/assets/images/three/buildings/obelisks.png)         |__Obelisks__       |||
|![Stage](/assets/images/three/buildings/stage.png)               |__Stage__          |WorkerUserComponent<br/>LayerAffectorWorking|Worker: Entertainer Quantity: 1 Queue: 2 Duration: 20<br/>Layer: Entertainment Value: 100 Range: 10|
|![Garden](/assets/images/three/buildings/garden.png)             |__Garden__         |LayerAffector|Layer: Desirability Value: 10 Range: 3 Falloff: 3|
|![RoadBlocker](/assets/images/three/buildings/roadBlocker.png)   |__Road Blocker__   |HousingComponent|Health: 100|
|![Bridge](/assets/images/three/buildings/bridge.png)   |__Bridge__   |||

## Structures

|![Tree](/assets/images/three/structures/tree.png) |__Tree__        |StructureCollection<br/>LayerAffector|Key: TRE Destr: 1 Deco: 0 Walk: 0 Size: 1<br/>Layer: Desirability Value: 5 Range: 2 Falloff: 2|
|![Ore](/assets/images/three/structures/ore.png) |__Ore__           |StructureCollection<br/>LayerAffector|Key: ORE Destr: 0 Deco: 0 Walk: 0 Size: 2<br/>Layer: Iron Value: 10 Range: 1|
|![Rubble](/assets/images/three/structures/rubble.png) |__Rubble__  |StructureCollection|Key: RUB Destr: 1 Deco: 1 Walk: 0 Size: 1|

## Walkers

### Migration

|__ImmigrationWalker__  |ImmigrationWalker  |Path: Map Capacity: 5|
|__EmigrationWalker__   |EmigrationWalker   |Path: Map Capacity: 5|
|__HomelessWalker__     |HomelessWalker     |Path: Road Capacity: 1|

### Roaming

|__WaterWalker__      |ServiceWalker    |Path: RoadBlocked Service: Water Amount: 100/s|
|__CollapseWalker__   |RiskWalker       |Path: RoadBlocked Risk: Collapse Amount: 100/s|
|__DiseaseWalker__    |RiskWalker       |Path: RoadBlocked Risk: Disease Amount: 100/s|
|__SickWalker__       |RiskWalker       |Path: Road Risk: Disease Amount: -10/s|
|__FireWalker__       |RiskWalker       |Path: RoadBlocked Risk: Fire Amount: 100/s|
|__TreasureWalker__   |CollectionWalker |Path: RoadBlocked Items: Gold|
|__SaleWalker__       |SaleWalker       |Path: RoadBlocked Storage: 1 Unit|
|__EmploymentWalker__ |EmploymentWalker |Path: RoadBlocked Return: 1|

### Logistics

|__DeliveryWalker__     |DeliveryWalker |Path: Road Storage: 1 Unit Return: 1|
|__StorageWalker__      |StorageWalker  |Path: Road Storage: 1 Unit Return: 1|
|__PurchaseWalker__     |PurchaseWalker |Path: Road Storage: 2 Unit|

### Workers

|__LabourWalker__      |WorkerWalker    |Path: Road Worker: Laborer Storage: 1 Unit|
|__MasonWalker__       |WorkerWalker    |Path: Road Worker: Mason Storage: 1 Unit|
|__EntertainerWalker__ |WorkerWalker    |Path: Road Worker: Entertainer Storage: 1 Unit|

## Items

|![Gold](/assets/images/three/items/gold.png)       |__Gold__     |Key: GLD Unit Size: 1|
|![Potato](/assets/images/three/items/potato.png)   |__Potato__   |Key: PTT Unit Size: 100|
|![Meat](/assets/images/three/items/meat.png)       |__Meat__     |Key: MEA Unit Size: 100|
|![Iron](/assets/images/three/items/iron.png)       |__Iron__     |Key: IRN Unit Size: 1|
|![Tools](/assets/images/three/items/tools.png)     |__Tools__    |Key: TOL Unit Size: 10|
|![Granite](/assets/images/three/items/granite.png) |__Granite__  |Key: GRT Unit Size: 1|
