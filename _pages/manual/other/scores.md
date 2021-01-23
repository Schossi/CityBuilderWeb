---
permalink: /manual/scores
title: "Scores"
sidebar:
  title: "Manual"
  nav: manual
---

Scores represent all kinds of numerically quantifiable values for a city. 
They are used for displaying statistics to the player and checking win conditions.  
The different Score Scripts each implement a way of calculating a score value. They are available as ScriptableObjects in the CityBuilder/Scores Context Menu.  
  
You can easily create your own scores by inheriting from Score and implementing the Calculate Method.  

Some of the Scores included in CCBK are:

### Average Building Score  
Calculates the average value from different values assigned to Buildings
> Tent:0 Hut:50 Palace:100 > 1xTent 2xHut 2xPalace = 60 Housing Quality  

### Average Service/Risk Score  
Averages out the risk/service value of a defined building category  
> how well are housings supplied with water, whats the general risk of collapse across my city, ...  

### Building, Item, Population Score  
Just counts the number of a building that exist.
> how many pyramids have been built, how many diamonds stored, how many plebs live in town, ...  

### Coverage Score
Calculates the number of people buildings would cover against the current population count
> 1 temple covers 1x100 , 2 shrines cover 2x50 > population=400 => 50% Coverage  

### Multiplied, Summed, Threshold Score  
can be used to transform other scores
> culture = entertainment + monuments, different threshold of employment, ...  