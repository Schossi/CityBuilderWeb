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

Housing is built using the BuildingBuilder in IngameUI/Tools/HouseTool. Which building a BuildingBuilder builds is determined by the BuildingInfo field. In this case that is PropertyInfo so a Property building will be placed by the tool.  

The Property building has a HousingPlaceholderComponent that just waits to be occupied and then replaces the building the lowest tier of actual housing(Tent). The occupation happens when an ImmigrationWalker arrives at the building. These ImmigrationWalkers are spawned by the Migration behaviour in PlebMigration as long as the sentiment is good enough. The sentiment in THREE is calculated in the MigrationScore which is a combination of housing quality, food safety and employment.  
  
Tents and all the other, higher types of housing have a HousingComponent which determines how many people of a population type each of them has capacity for. These population quantities can then be used in buildings that need employment to work. In THREE there is only one Population type called Plebs.  
  
The housings also have an EvolutionComponent that refers to the HousingEvolution EvolutionSequence. This EvolutionSequence specifies what any of its stages needs to evolve to the next one. To evolve to a Hut the Tent needs access to the WaterService and the DesirabilityLayer needs to have a value of at least 5 in the location of the Tent. So we need to place a Well that can reach the Tent and a Garden close to it to make it evolve.  
  
The third building component all housings have in common is the RiskerComponent which defines which Risks can proc on a building and how fast the risk value increases. The Tent has a CollapseRisk which makes terminates the building and replaces it with rubble and a DiseaseRisk which places an addon on the building that sends out DiseaseWalkers that infect other houses and eventually kills its occupants.  
  
Only the highest tier housing(Villa) has a GeneratorComponent which generates Gold at certain intervals that can be collected by Treasurers.

### Risks&Services

|![Well](/assets/images/three/buildings/well.png)               |__Well__         |EmploymentComponent<br/>ServiceWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: WaterWalker|
|![Workshop](/assets/images/three/buildings/workshop.png)       |__Workshop__     |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: CollapseWalker|
|![Firefighter](/assets/images/three/buildings/firefighter.png) |__Firefighter__  |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: FireWalker|
|![Doctor](/assets/images/three/buildings/doctor.png)           |__Doctor__       |EmploymentComponent<br/>RiskWalkerComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: DiseaseWalker|
|![Treasurer](/assets/images/three/buildings/treasurer.png)     |__Treasurer__    |EmploymentComponent<br/>CollectionComponent|Group: Services Needed: 5 Plebs<br/>Downtime: 5 Prefab: TreasureWalker Storage: Global|

These Buildings all have an EmploymentComponent which specifies how many Plebs are needed for the Building to fully function. Unless they are fully staffed they wont send out walkers that perform their various functions.  
  
The Well sends out a Walker that provides the WaterService that is needed for housing higher than Tents. The Workshop, Firefighter and Doctor send out walkers that prevent different Risks from happening in buildings they pass. The Treasurer sends out a walker that collects the Gold that is generated in Villas.

### Food

|![Farm](/assets/images/three/buildings/farm.png)     |__Farm__   |EmploymentComponent<br/>ProductionComponent<br/>LayerEfficiencyComponent|Group: Food Needed: 15 Plebs<br/>Interval: 10 Produces: 100 Potatoes<br/>Layer: Water Min: 0.2 Max: 100|
|![Hunter](/assets/images/three/buildings/hunter.png) |__Hunter__ |EmploymentComponent<br/>ItemsRetrieverComponent|Group: Food Needed: 10 Plebs<br/>Retriever: HunterWalker Downtime: 10|
|![Silo](/assets/images/three/buildings/silo.png)     |__Silo__   |EmploymentComponent<br/>StorageComponent|Group: Logistics Needed: 10 Plebs<br/>Storage: Stacked StackCount: 6 Capacity: 4 <br/>Orders: Accept Potato, Meat|
|![Market](/assets/images/three/buildings/market.png) |__Market__ |EmploymentComponent<br/>DistributionComponent|Group: Services Needed: 10 Plebs<br/>Storage: Unit Capped Capacity: 5 MinimumOrder: 1 Orders: Fill Potato, Meat|

To evolve from Huts to Houses the housings need one type of food, to get to the Villa level two different types are needed.  
  
Farms have a ProductionComponent that generate potatoes at a certain interval which is influenced by the buildings efficiency. The EmploymentComponent lowers building efficiency when the building is not fully staffed. The LayerEfficiencyComponent influences building efficiency based on the value of the WaterLayer at the position of the building. This means Farms work better when they are closer to Water(because of the AffectingTile in the DefaultLayerManager in Logic) and when it rains(RainWater LayerModificationHappening).  
  
Hunters have a ItemsRetrieverComponent that sends out HunterWalkers that look for BLB dispensers. These dispensers are wanderers that get created by the TilemapSpawner of Grid/Ground and destroyed when the SingleItemsDispenser on the is used by a hunter.  

Both Farms and Hunters have DeliveryWalkers that try to deliver their produced food to the closest Silo(IItemReceiver). If they don't find one that has space for their items they just just stand around and retry until they eventually vanish.  
  
To get food from Silos to housing a Market is needed. It sends out SaleWalkers that check what the housings they pass need. PurchaseWalkers then try to find the needed items at the closest Silo(IItemGiver) and take it back to the market. SaleWalkers then fill up on these Items before they next head out, they will then give those Items to any housing they pass that needs them(IItemRecipient).  
  
Notice the different walkers we have used in this category. The HunterWalker walks around the map which is specified by setting Map as its PathType in the HunterWalkerInfo. SaleWalkers are roaming walkers(RoamingWalker>BuildingComponentWalker>SaleWalker) that use PathType RoadBlocked so they have to use the road and can be blocked. PurchaseWalkers are destination walkers that use the Road PathType so the also use the road network but can walk over generic road blockers.

### Production

|![IronMine](/assets/images/three/buildings/ironMine.png)       |__Iron Mine__    |EmploymentComponent<br/>ProductionComponent|Group: Production Needed: 10 Plebs<br/>Interval: 20 Produces: 1 Iron|
|![GraniteMine](/assets/images/three/buildings/graniteMine.png) |__Granite Mine__ |EmploymentComponent<br/>ProductionComponent|Group: Production Needed: 10 Plebs<br/>Interval: 20 Produces: 1 Granite|
|![Smith](/assets/images/three/buildings/smith.png)             |__Smith__        |EmploymentComponent<br/>ProductionComponent<br/>RiskerComponent|Group: Production Needed: 10 Plebs<br/>Interval: 10 Consumes: 1 Iron Produces: 10 Tools<br/>FireRisk 3/s|
|![Yard](/assets/images/three/buildings/yard.png)               |__Yard__         |EmploymentComponent<br/>StorageComponent|Group: Logistics Needed: 10 Plebs<br/>Storage: Stacked StackCount: 8 Capacity: 4 <br/>Orders: Accept Iron, Tools, Granite Refuse Potato, Meat|

The production buildings in THREE produce goods that are eventually needed to build the Obelisk monument. The GraniteMine produces Granite items which are directly needed in the building process of the Obelisks. The IronMine produces Iron which has to be refined by a Smith to Tools which are needed for Labour workers to spawn. The Smith also has a RiskerComponent with FireRisk so it needs a Firefighter nearby or it will go up in flames.  
  
The items a StorageComponent can store are defined in the Orders field. For example the Silo does not have any order for Iron so it will never store it. The StorageYard on the other hand has an order for every item but the orders for Food have a ratio of 0. This ratio can be changed by the player so yards can theoretically also be used to store food.  
  
The mines both have building requirements that specify where on the map they can be built. The GraniteMineInfo has a building requirement with Mode All that has the Granite tile as a ground option. This means that every point of the Granite Mine has to be built on a Granite tile. The IronMine specifies Any with count 1 and a layer requirement for the IronLayer between 5 and 999. Therefore at least one point of the IronMine has to be built on a point with an IronLayer value of at least 5.

### Workers

|![LabourCamp](/assets/images/three/buildings/labourCamp.png)           |__Labour Camp__      |CyclicWorkerProviderComponent<br/>ItemEfficiencyComponent|Prefab: LabourWalker Downtime: 5<br/>Item: Tools Interval: 10|
|![MasonCamp](/assets/images/three/buildings/masonCamp.png)             |__Mason Camp__       |PooledWorkerProvider|Prefab: MasonWalker Count: 2 Downtime: 3|
|![EntertainerCamp](/assets/images/three/buildings/entertainerCamp.png) |__Entertainer Camp__ |CyclicWorkerProviderComponent<br/>RiskerComponent<br/>LayerAffector|Prefab: EntertainerWalker<br/>Risk: Fire Increase: 5/s<br/>Layer: Desirability Value: -10 Range: 3 Falloff: -3|

These buildings all spawn worker walkers that can be used in IWorkerUsers, which workplace can use which worker is defined by the Worker object that is set in WorkerWalker.Worker. There is a small difference between the spawners in Labour- and EntertainerCamp and the one used in the MasonCamp. CyclicWorkerProviders send out 'fire and forget' walkers in fixed intervals(influenced by efficiency) while the PooledWorkerProvider has a certain number of walkers that return to the building and go back out after a cooldown.

### Other

|![ObelisksSite](/assets/images/three/buildings/obelisksSite.png) |__Obelisks Site__  |MonumentSiteComponent|Stages: CirclyPits, CenterPit, CircleObelisk, CenterObelisk<br/>various steps with different workers per stage|
|![Obelisks](/assets/images/three/buildings/obelisks.png)         |__Obelisks__       |||
|![Stage](/assets/images/three/buildings/stage.png)               |__Stage__          |WorkerUserComponent<br/>LayerAffectorWorking|Worker: Entertainer Quantity: 1 Queue: 2 Duration: 20<br/>Layer: Entertainment Value: 100 Range: 10|
|![Garden](/assets/images/three/buildings/garden.png)             |__Garden__         |LayerAffector|Layer: Desirability Value: 10 Range: 3 Falloff: 3|
|![RoadBlocker](/assets/images/three/buildings/roadBlocker.png)   |__Road Blocker__   |RoadBlockerComponent|Separate Tags for every roaming walker|
|![Bridge](/assets/images/three/buildings/bridge.png)   |__Bridge__   |||

An ObeliskSite has a MonumentSiteComponent which defines all the different stages of building, these different stages and their steps define which workers and items are needed and where. When one stage is completed the monument site progresses to the next one until finally it is replaced by the finished Obelisks building.  

The Obelisks building does not have any function of its own. It is just used in the MonumentScore for 100 points. In Mission3 having a MonumentScore of 100 is set as the win condition so as soon as the Obelisks are built that mission is won.  
  
Stages are WorkerUserComponents that use the Entertainer worker type. Each worker that arrives at a stage keeps if functional for a while. The stage also has a LayerAffectorWorking which increases the EntertainmentLayer value around it as long as the building is working. That entertainment value is needed to evolve Houses to Villas.  
  
Gardens are simple buildings that just increase the desirability layer values around them, this is needed to evolve housing from Tents to Houses.  
  
A RoadBlockerComponent can be used to block walker from using the points on a road under it. The one in THREE has different WalkerInfos set in its Tags which results in only those walkers being blocked. In addition when the RoadBlocker is clicked by a player it is possible which of the tags is actually active in the dialog.  
  
Bridges are special buildings that let walkers pass over them. They let walkers with PathType Road pass be registering the points they occupy as a road using the StructureRoadRegisterer and they let map walkers pass by having a OffMeshLink that is used be the NavMesh. They are special because they can have different sizes, to do this their BuildingInfo is a ExpandableBuildingInfo, their Building is an ExpandableBuilding and they are built using an ExpandableBuilder. Another special feature bridges have is the height override on Bridge/Pivot/Height which forces any walker that collides with its box collider to a certain height.

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
