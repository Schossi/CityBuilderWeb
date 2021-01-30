---
permalink: /manual/scratch
title: "Start from Scratch"
layout: single
classes: ''
toc: true
toc_label: "Chapters"
toc_icon: city
toc_sticky: true
sidebar:
  title: "Manual"
  nav: manual
---

Throughout the following steps we will create a very simple oldschool city builder from scratch using CCBK. Please forgive the horrible programmer art.

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-28T21:10:27.956Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;r5YPFfMA3hvyD7RFzXTe\&quot; version=\&quot;14.2.6\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;e1Ed8QitaK_qdH0PmYRJ\&quot; name=\&quot;evolution\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

This page covers only the first two evolutions, water and food. A completed version with all stages can be found in the CityBuilderManual project. I believe you will be able to figure the rest out after following the steps laid out here. Religion is very similar to water and pottery has just a slightly longer production chain than food.

## Setup

* Create a new unity project using the 2D template
* Import the CCBK Core Framework  
![Import](/assets/images/scratch/1Import.png)
* Place the [Manual Assets][1] inside your Assets folder

[1]:{{ site.url }}/assets/downloads/manualAssets.zip

## Map

* Create a Gameobject at 0,0,0 and call it 'Map'
* Add a Grid Component
* Add a DefaultMap Component [^1]
  * Set its Size to 32x32
  * In Walking- and BuildingBlockingTiles add the water tile [^2]
  * Create a child Gameobject at 0,0,0 and call it 'Ground'
    * Add Tilemap and TilemapRenderer to it
  * Assign it to the Ground field on your map
* Move the Main Camera Object to the center of the map (16,16,-10)
  * Add a Camera Controller Component to it
* Open the Tile Palette Tab found in Windows/2D
  * Make sure your active Tilemap is 'Ground' and your Palette is 'historic'
  * Draw your map inside the guide lines of the map(turn on gizmos if you cant see it)

![Ground](/assets/images/scratch/2Ground.png)  
We'll later add a water layer that spreads out two tiles from water. I' ve drawn grass tiles there to communicate that to the player.

With all that done you can start the game for the first time. You should be able to move the Camera around the map while being confined to its bounds.

## Roads

Roads are generally pretty simple but we'll have to do some setup on the Tools and Logic side to be able draw them so please bear with me.

### Tilemap
{:.no_toc}
* Create a child Gameobject in Map at 0,0,0 and call it 'Roads'
  * Add Tilemap and TilemapRenderer to it
    * Set OrderInLayer to 1
  * Add a DefaultRoadManager Component
* Create a child Gameobject in Map at 0,0,0 and call it 'Highlights'
  * Add Tilemap and TilemapRenderer to it
    * Set OrderInLayer to 2
  * Add a DefaultHighlightManager to it
    * Assign the Highlight Tiles of the same name  

### Logic
{:.no_toc}

* Create a Gameobject at 0,0,0 and call it 'Logic' and add the following Components
  * DefaultGameManager
  * ObjectRepository
  * DefaultStructureManager

### Road Object
{:.no_toc}
* Create a Folder in your Assets called City
  * Create a Road Object  
Found in the ContextMenu under Create/CityBuilder/Road
  * Add a single stage to it by assigning 1 to Stages-Size
    * Assign 'ROD' to the Key [^3]
    * Assign the 'road' tile to Tile
* On ObjectRepository assign Road

### UI Tools
{:.no_toc}
* Create a UI/Panel and call it 'Tools'
  * Move it to middle-right with a width of 50
  * Add a VerticalLayoutGroup and a ContentSizeFitter with verticalFit=Preferred
  * Add a ToggleGroup with AllowSwitchOff=1 and a ToolsManager Component
    * Assign the ToggleGroup in the ToolsManager
  * Create a UI/Toggle in Tools and call it 'RoadTool'
    * Delete the Text
    * Resize the Toggle to 50,50
    * Assign the ToggleGroup
    * Set the Toggles IsOn to false
    * Move Background and Checkmark to middle-center with size 32,32
    * Assign toolsBorder as the Checkmark image and blank as the Background
    * Add a RoadBuilder and ToolsActivator Component to RoadTool
      * Assign the Road Object you just created in the Road field
    * Add ToolsActivator.SetToolActive to the Toggles OnValueChanged event

After selecting the tool and starting up the game you should now be able to draw roads on the map.  
![Roads](/assets/images/scratch/3Roads.png)  

## Buildings

### Prefab
{:.no_toc}
* Create a Gameobject at 0,0,0 and call it 'WaterSupply' [^4]
  * Create a 2D Object/Sprite at 1,1,0 and call it 'sprite'
    * Assign the waterSupply sprite and OrderInLayer 10
  * Add a Building Component to WaterSupply and assign sprite as its Pivot
* Create a Folder called 'Buildings' inside the City Folder
  * Drag the WaterSupply to the Folder to create a Prefab
  * Remove the WaterSupply from the Scene

### Buildinginfo
{:.no_toc}
* Create a BuildingInfo Object called 'WaterSupply' in Buildings  
Found in the ContextMenu under Create/CityBuilder/BuildingInfo)
  * Assign Key='WAT' Name='water supply' and Size=2,2
  * Assign the Prefab we just created
* On the WaterSupply Prefab assign the BuildingInfo

### Tool
{:.no_toc}
* Duplicate the RoadTool we've created in the previous chapter and call it 'WaterTool'
  * Replace the RoadBuilder with a BuildingBuilder [^5]
    * Assign the WaterSupply BuildingInfo to the BuildingBuilder
  * Set the Background image to waterSupply and reset the color to white

### Logic
{:.no_toc}
* Add a DefaultBuildingManager to Logic

Start up the game again and build some water supplies!
![Buildings](/assets/images/scratch/4Buildings.png)  

## Walkers

### Prefab
{:.no_toc}
* Create a Gameobject at 0,0,0 and call it 'WaterCarrier' 
  * Create a child Gameobject at 0.5,0.5,0 and call it 'pivot'[^6]
    * Create a 2D Object/Sprite at 0,0,0 and call it 'sprite'
      * Assign the waterCarrier sprite and OrderInLayer 20
      * Set Z Rotation to 270
  * Add a ServiceWalker Component to WaterCarrier and assign pivot as its Pivot
    * Set PathType to Road
* Create a Folder called 'Walkers' inside the City Folder
  * Drag the WaterCarrier to the Folder to create a Prefab
  * Remove the WaterCarrier from the Scene

### Walkerinfo
{:.no_toc}
* Create a WalkerInfo Object called 'WaterCarrier' in Walkers (found in the ContextMenu under Create/CityBuilder/WalkerInfo)
  * Assign Name='water carrier'
* On the WaterCarrier Prefab assign the WalerInfo

### Spawning
{:.no_toc}
* On the WaterSupply Prefab add a ServiceWalkerComponent Component[^7]
  * Assign Count=1 Reuse=1 Downtime=5

As soon as a WaterSupply is connected to a road it should now spawn a WaterCarrier that roams around for a bit and then returns.
![Walkers](/assets/images/scratch/5Walkers.png)  
* Change Variance on the Map to 0.2 and start the game again, walkers should now be offset a little bit to prevent overlapping

## Templates

Since we will be creating a number of Buildings and Walkers in the following Chapters let's create blank templates for them that we can easily duplicate.[^4]
* Duplicate WaterSupply Prefab and Info
  * rename them both to 'Building'
  * clear out key, name and prefab in info
  * clear out info and sprite in prefab
  * remove the ServiceWalkerComponent
* Duplicate WaterCarrier Prefab and Info
  * rename them both to 'Walker'
  * clear out name in info
  * clear out info and sprite in prefab
  * remove the ServiceWalker

From now on whenever i mention creating a new building do the following.
* Duplicate Building Prefab and Info
* Set prefab, key and name in info
* Set info and sprite in prefab

Whenever i mention creating a new walker do the following.
* Duplicate Walker Prefab and Info
* Add whatever Walker Component is needed
* Set name in info
* Set info and sprite in prefab

## Housing

### Population Object
{:.no_toc}
* Create a Population Object in your City Folder  
Found in ContextMenu under Create/CityBuilder/Population
  * Set Key='POP' Name='Population'
* On ObjectRepository assign Population

### Buildings
{:.no_toc}

* Create Buildings

|name|info-key|info-name|sprite|
|----|----|----|----|
|H0|HNO|housing|housing|
|H1Hut|HUT|hut|hut|
|H2Shanty|SHT|shanty|shanty|
|H3Cottage|CTG|cottage|cottage|

* Add a HousingPlaceholderComponent to H0
  * Assign H1 as the Prefab
* Add a HousingComponent to H1,H2,H3
  * In PopulationHousings add a single entry that uses the Population Object and the counts 20, 35, 50

### Walkers
{:.no_toc}

* Create Immigrant Walker
  * Add ImmigrationWalker Component
    * Name: immigrant Sprite: migrant
    * Set PathType to MapGrid
    * Set Capacity to 10

### Logic
{:.no_toc}

* Add DefaultPopulationManager to Logic
* Add a Migration to Logic
  * Assign the ImmigrationWalker and set the count to 100
  * Set Logic as the Entry
  * Assign the Population Object

### Tool
{:.no_toc}

* Duplicate the WaterTool and name it HousingTool
* Assign H0 as the Building
* Use the hut sprite as the Background
* Move it between RoadTool and WaterTool

Start the game, the HousingTool now builds placeholders that are turned into huts as soon as immigrants arrive.  
![Housing](/assets/images/scratch/6Housing.png)  

## Food

### Items
{:.no_toc}

* Create a Folder called 'Items' inside the City Folder
* Create an Item Object in the Items Folder  
Found in ContextMenu under Create/CityBuilder/Item
  * Set Key='CHK' Name='chickpeas' UnitSize=100 Icon=chickpeas
* On ObjectRepository assign Item  

* Create a Gameobject at 0,0,0 and call it 'Chickpeas'
  * Set scale to 0.65,0.65,1
  * Create 4 Sprites with OrderInLayer 30 and assign the chickpeas1-4 sprites
  * Add a StorageQuantityVisual
    * Set Swap to true
    * Add the sprites to the Objects array
* Drag Chickpeas to the Items Folder and remove it from the scene
* Add it to the Chickpeas-Item Visuals

### Walkers
{:.no_toc}

|name|info-name|sprite|component|settings
|----|----|----|----|----|
|CartPusher|cart pusher|cartPusher|DeliveryWalker|PathType:Road|
|BazaarBuyer|bazaar buyer|bazaarBuyer|PurchaseWalker|PathType:Road Capacity:3|
|BazaarSeller|bazaar seller|bazaarSeller|SaleWalker|PathType:RoadBlocked|

### Buildings
{:.no_toc}

|name|info-key|info-name|sprite|
|----|----|----|----|
|Farm|FAM|farm|farm|
|Granary|GRN|granary|granary|
|Bazaar|BAZ|bazaar|bazaar|  

* Granary and Farm are larger buildings so we'll have to adjust size and pivot position
  * Farm size:3x3 pivot:1.5,1.5,0
  * Granary size:4x4 pivot:2,2,0
* Farm
  * Add a ProductionComponent
    * Set Interval to 20
    * Assign the CartPusher as Prefab in DeliveryWalkers
    * Create an entry in ItemsProducers
      * Set Item to Chickpeas and Quantity to 100
      * Set Storage to FreeUnityCapped with Capacity:1
  * Add a ProgressThresholdVisualizer 
    * Create 4 Sprites under sprite with OrderInLayer:100 and assign farmProgress1-4 sprites
    * Create 4 entries in ProgressThresholds with the above sprites and the thresholds: 0.2, 0.4, 0.6, 0.8

* Granary
  * Add a StorageComponent
    * Set Storage to Stacked Mode with 8 Stacks and 4 Capacity
    * Create an entry in Orders for Chickpeas with Ratio:1
  * Add a StorageQuantityVisualizer to Granary
    * Create 8 Transforms and move them over the centers of the holes in the sprite
    * Add them to the Origins array

* Bazaar
  * Add a DistributionComponent
    * Set Storage to FreeUnitCapped with Capacity 5
    * Create an entry in Orders for Chickpeas with Ratio:1
    * Assign the BazaarBuyer as Prefab in PurchaseWalkers
    * Assign the BazaarSeller as Prefab in SaleWalkers with Reuse:1 and Downtime:5
<br/><br/><br/>
* Add DefaultItemManager to Logic and set Storage to Free Mode
* Duplicate the WaterTool 3 times and assign the sprites and BuildingInfos of Farm, Granary and Bazaar

Build some farms and watch them grow. Connect them to a granary for the chickpeas to be stored there. The Bazaar wont do anything because the seller wont find anyone in need of chickpeas yet.  
![Food](/assets/images/scratch/7Food.png)  

## Layer

* Create a Layer Object in the City Folder and name it Water  
Found in ContextMenu under Create/CityBuilder/Layer
* On Logic Add DefaultLayerManager
  * Create an Entry in AffectingTiles  
assign the water tile, water layer and set value:10 Range:2 Falloff:0 
* In the BuildingInfos of Farm and WaterSupply add a LayerRequirement entry
  * Set Layer:Water Min:5 Max:100

Farms and WaterSupplies can now only be built close to water.

## Evolution

### Water Service
{:.no_toc}

* Create a Folder called 'Services' inside the City Folder
* Create a Service Object in the Services Folder and name it Water  
Found in ContextMenu under Create/CityBuilder/Service
* In the WaterCarrier Walker Prefab assign the Water Service

### Evolution Sequence
{:.no_toc}

* Create an EvolutionSequence Object in the City Folder  
Found in ContextMenu under Create/CityBuilder/Service
* Add the following Stages
  * BuildingInfo: H1Hut
  * BuildingInfo: H2Shanty  Services: Water
  * BuildingInfo: H3Cottage Items: Chickpeas

### Evolution Component
{:.no_toc}

* Add an EvolutionComponent to all 3 Housing Buildings(H1, H2, H3)
* Assign the EvolutionSequence
* Add a ServiceRecipient for Water to all 3 with a Loss of 5
* Add an ItemsRecipient for Chickpeas to H2 and H3  
Set Storage to FreeItemCapped Mode with Capacity 10 and ConsumptionInterval to 2  

Start up the game and combine everything to evolve the housing to Cottages
![Evolution](/assets/images/scratch/8Evolution.png)  

## Saving

* Create a BuildingInfoSet Object in the Buildings Folder  
Found in ContextMenu under Create/CityBuilder/Sets/BuildingInfoSet
* On ObjectRepository assign Buildings with it.  

Thats all we were missing for saving and loading. In the absence of any UI you can use the In-Editor Buttons on Logic/DefaultGameManager to save and load.

<br/><br/>

[^1]: CCBK supports XYZ and XZY swizzles, the default XYZ is good for 2D 
[^2]: blocking and ground are needed later to prevent walking and building on water 
[^3]: keys have to be unique within their category, they are mostly used for saving 
[^4]: the completed project uses a tree of prefab variants for buildings(skipped here for brevity)
[^5]: switch the inspector to debug and select the other script, switch inspector back to normal 
[^6]: sprite is a separate object in this one because is drew the walkers in the wrong direction and they have to be rotated
[^7]: i know