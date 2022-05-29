---
permalink: /manual/defense
title: "2D Tower Defense"
sidebar:
  title: "Manual"
  nav: manual
---

Art assets have been adapted from packs made by [Kenney](https://kenney.nl)

Play it [here]({% link _pages/demos/demoDefense.md %}), primarily uses the [attacks]({% link _pages/manual/systems/attacks.md %}) and items retriever [resource]({% link _pages/manual/systems/resources.md %}) systems.

## Buildings

|![Center](/assets/images/defense/defenseCenter.png)|__Center__|AttackableComponent|Health: 100|
|![Tower](/assets/images/defense/defenseTower.png)|__Tower__|DefenderComponent|Distance: 2<br/> Cooldown: 1.5<br/> Damage: 2|
|![Lumberjack](/assets/images/defense/defenseLumberjack.png)|__Lumberjack__|ItemsRetrieverComponent|Storage: Global<br/> Walker: LumberjackWalker|
|![StoneQuarry](/assets/images/defense/defenseStoneQuarry.png)|__Stone Quarry__|ItemsRetrieverComponent|Storage: Global<br/> Walker: StoneQuarryWalker|

The Center building in the defense demo just has an AttackableComponent with a certain health. Since the AttackableComponent implements and registers the IAttackable trait it will be the be targeted by attackers. IAttackable is also used to check if the game is over. Whenever a building is removed the DefenseManager checks if there are any IAttackables left and if not it will end the game.

Towers use the DefenderComponent which periodically queries the IAttackManager for attackers in its range. If one is found the DefenderComponent will hurt it for its Damage and show a line between them for 0.1s.

The Lumberjack and StoneQuarry buildings periodically send out ItemsRetrieverWalkers that look for dispensers with different keys(TRE/STO). Theses buildings use storage mode Global which means that the items brought back by the walkers are stored in one shared ItemStorage instead of the building itself. That global storage is then used by the BuildingBuilders in IngameUI/Tools when building and by the InventoryVisualizers in IngameUI/Wood/Text and IngameUI/Stone/Text.

## Structures

|![Wall](/assets/images/defense/defenseWall.png)|__Walls__|StructureTiles|Key: STO Replicates to WallObstacles|
|![Trees](/assets/images/defense/defenseWood.png)|__Trees__|StructureCollection<br/>Tree > ReloadingItemsDispenser|Key: TRE Prefab: Tree<br/>Key: TRE Charges: 1 Reload: 5|
|![Rocks](/assets/images/defense/defenseStone.png)|__Rocks__|StructureCollection<br/>Rock > ReloadingItemsDispenser|Key: ROK Prefab: Rock<br/>Key: STO Charges: 1 Reload: 5|

Walls are StructureTiles found in Grid/Walls. When the game starts a StructureTiles structure checks for all the points in the tilemap that have the tile they use. Whenever a point is added or removed from the structure it also changes the tilemap accordingly. Walls also replicate to another structure so any point added to it will also be added to WallObstacles. WallObstacles place gameobjects on the map that have a NavMeshObstacle. That is no longer really necessary because nothing in the defense demo currently uses Map pathing but is left in just as a demonstration.

Trees and Rocks are simple StructureCollections that have a gameobject at every one of their points. These gameobjects(Tree/Rock) contain a ReloadingItemsDispenser that can be used by the walkers sent out by the Lumberjack and StoneQuarry walkers. When they are used they return the items that have been set in the Items field. They also wait out the specified ReloadTime before they can be used again.

## Walkers

|![AttackWalker](/assets/images/defense/defenseAttackWalker.png)|__AttackWalker__|AttackWalker|Path: MapGrid Speed: 3<br/>Health: 10 Damage: 5 Rate: 5|
|![LumberjackWalker](/assets/images/defense/defenseWoodWalker.png)|__LumberjackWalker__|ItemsRetrieverWalker|Path: Map Speed: 2<br/>Distance: 10 DispenserKey: TRE|
|![StoneQuarryWalker](/assets/images/defense/defenseStoneWalker.png)|__StoneQuarryWalker__|ItemsRetrieverWalker|Path: Map Speed: 2<br/>Distance: 10 DispenserKey: STO|

## Items

|![Stone](/assets/images/defense/defenseStone.png)|__Stone__|
|![Wood](/assets/images/defense/defenseWood.png)|__Wood__|