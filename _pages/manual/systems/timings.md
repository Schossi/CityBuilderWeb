---
permalink: /manual/timings
title: "Timings"
sidebar:
  title: "Manual"
  nav: manual
---

This system provides interactions with the current Playtime.  
  
>time display in years, days, ..  
>happenings like catastrophes or blessings  
>time based weather and lighting  
  
## Units

Created using ContextMenu > CityBuilder-TimingUnit these determine how the playtime is partitioned. TimingUnits can be repeating(DayOfWeek, Month, ...) or endless(Year). Use the PlaytimeVisual to visualize the progress of a TimingUnit in the UI. 

## Happenings

Various events that happen at predefined times. Some Happenings have a one off effect at their start or end while others may be active for a period. The different Happenings coming with CCBK can be found in ContextMenu > CityBuilder-Happenings. They are then added to Missions along with a condition that determines when they happen. This means that a Happening may be reused a number of times throughout missions. Adding a title and description to a happening may trigger a dialog at the happenings start or end that display them.  

Happenings are relatively easy to extend. Create a new script and derive from the TimingHappening base class. For a Happening that executes once at its start or end override Start or End, for an ongoing effect override Activate and Deactivate.(ie rain from hour 2-3 is an Activate/Deactivate, an earthquake that destroy some buildings at the start of hour 2 uses Start) Check out all the existing Happenings in CityBuilderCore.Systems.Timings.Happenings for examples.