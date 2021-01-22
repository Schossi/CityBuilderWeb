---
permalink: /manual/views
title: "Views"
sidebar:
  title: "Manual"
  nav: manual
---

Views are different ways to highlight systems and show additional information to the player. They are available as ScriptableObjects in the CityBuilder/Scores Context Menu.  

You can easily create your own views by inheriting from View and implementing the Activate and Deactivate Methods.  

The views included in CCBK are:

### View Bar Risk/Service
Adds bars to all buildings that show the current service/risk value.  
Among the risk/service to visualize the bar to visualize them with can be set.  
CCBK includes ScaledValueBar that visualizes Values by scaling a transform along the Y Axis. You can create your own Bar(eg three flame sprites that indicate risk of fire) by inheriting from BaseValueBar.
> bars that empty with water service value, bars that rise with collapse or fire risk

### View Culling
Applies the specified camera culling when activated and resets it when deactivated.
> only show water walkers and wells in the water view  

### View Layer
Visualizes the values of a layer on the map by overlaying it with colors. The color for each point is selected from a gradient that is scaled to a minimum and maximum. Points with 0 value are skipped.
> heat layer that is visualized from blue to red between layer values of -20 and 40

### View Composite
Combines multiple other views.
> the water view shows the water layer, adds bars for the water service and hides objects unrelated to water