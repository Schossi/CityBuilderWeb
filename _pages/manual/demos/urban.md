---
permalink: /manual/urban
title: "2D City Sim"
sidebar:
  title: "Manual"
  nav: manual
---

Art assets have been adapted from sprites made by opengameart user [pixel32](https://opengameart.org/users/pixel32)

Play it [here]({% link _pages/demos/demoUrban.md %}).  

Demonstrated Connections, Multi-Road-Networks and Multi-Level-Structures.

## Buildings

|![Railstation](/assets/images/urban/railstation.png)|__Railstation__|RailwayComponent|Goods|OXX|
|![House](/assets/images/urban/house.png)|__House__|ConnectionPasserComponent<br/>LayerEfficiencyComponent<br/>HouseComponent|Power<br/>Water<br/>Van|OXX|
|![Shop](/assets/images/urban/shop.png)|__Shop__|ConnectionPasserComponent<br/>LayerEfficiencyComponent<br/>ShopComponent|Power<br/>Water<br/>Money|OXX|
|![WaterPump](/assets/images/urban/pump.png)|__Water Pump__|ConnectionPasserComponent<br/>ConnectionFeederComponent<br/>LayerEfficiencyComponent|Power<br/>Water<br/>Water|XXX|
|![PowerStation](/assets/images/urban/powerstation.png)|__Power Station__|ConnectionFeederComponent|Power|OXX|

## Structures

|![PowerLines](/assets/images/urban/powerLine.png)|__Power Lines__|StructureTiles<br/>ConnectionPasser|POW<br/>Power|OOX|
|![Pipes](/assets/images/urban/pipe.png)|__Pipes__|StructureTiles<br/>ConnectionPasser|PIP<br/>Water|XOO|

## Walkers

|![Train](/assets/images/urban/train.png)|__Train__|TrainWalker|Rail|
|![Truck](/assets/images/urban/truck.png)|__Train__|TruckWalker|Road<br/>100 Goods|
|![Van](/assets/images/urban/van.png)|__Train__|VanWalker|Road<br/>5 Goods|
