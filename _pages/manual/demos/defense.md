---
permalink: /manual/defense
title: "2D Tower Defense"
sidebar:
  title: "Manual"
  nav: manual
---

## Buildings

|![Center](/assets/images/defense/defenseCenter.png)|__Center__|AttackableComponent|Health: 100|
|![Tower](/assets/images/defense/defenseTower.png)|__Tower__|DefenderComponent|Distance: 2<br/> Cooldown: 1.5<br/> Damage: 2|
|![Lumberjack](/assets/images/defense/defenseLumberjack.png)|__Lumberjack__|ItemsRetrieverComponent|Storage: Global<br/> Walker: LumberjackWalker|
|![StoneQuarry](/assets/images/defense/defenseStoneQuarry.png)|__Stone Quarry__|ItemsRetrieverComponent|Storage: Global<br/> Walker: StoneQuarryWalker|

## Structures

|![Wall](/assets/images/defense/defenseWall.png)|__Walls__|StructureTiles|Key: STO Replicates to WallObstacles|
|![Trees](/assets/images/defense/defenseWood.png)|__Trees__|StructureCollection<br/>Tree > ReloadingItemsDispenser|Key: TRE Prefab: Tree<br/>Key: TRE Charges: 1 Reload: 5|
|![Rocks](/assets/images/defense/defenseStone.png)|__Rocks__|StructureCollection<br/>Rock > ReloadingItemsDispenser|Key: ROK Prefab: Rock<br/>Key: STO Charges: 1 Reload: 5|

## Walkers

|![AttackWalker](/assets/images/defense/defenseAttackWalker.png)|__AttackWalker__|AttackWalker|Path: MapGrid Speed: 3<br/>Health: 10 Damage: 5 Rate: 5|
|![LumberjackWalker](/assets/images/defense/defenseWoodWalker.png)|__LumberjackWalker__|ItemsRetrieverWalker|Path: Map Speed: 2<br/>Distance: 10 DispenserKey: TRE|
|![StoneQuarryWalker](/assets/images/defense/defenseStoneWalker.png)|__StoneQuarryWalker__|ItemsRetrieverWalker|Path: Map Speed: 2<br/>Distance: 10 DispenserKey: STO|

## Items

|![Stone](/assets/images/defense/defenseStone.png)|__Stone__|
|![Wood](/assets/images/defense/defenseWood.png)|__Wood__|