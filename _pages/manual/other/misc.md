---
permalink: /manual/misc
title: "Misc"
sidebar:
  title: "Manual"
  nav: manual
---

## Saving
CCBK includes a complete save and load system that serializes save data using unity's json serializer. The save data containers and save/load logic can generally be found in '#region Saving' at the end of the respective script.  
Save-/LoadData are perpetuated through the different systems starting at the central manager scripts. This means core components of CCBK like building components and walkers already have overridable Save/Load Methods that will be called without any extra work.  
The easiest way to hook data that is outside of CCBK into the save system is to inherit from ExtraDataBehaviour. The default game manager finds all those in its awake Method.

## Mission Parameters
Mission, Difficulty and MissionParameters are a proposal for managing different scenarios in your game.  
Mission and Difficulty are Scriptable Objects that can be defined in the Editor.  
MissionParameters includes all parameters needed to start a game and are passed to the IMissionManager when the scene is loaded.
