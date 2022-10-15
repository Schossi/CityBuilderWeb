---
permalink: /manual/walkers
title: "Walkers"
sidebar:
  title: "Manual"
  nav: manual
---

The primary way to move things about in CCBK.
> storage workers moving items, hunters collecting meat, architects inspecting buildings

An important field of the Walker Component is the Pivot. The Pivot is a transform in the center and root of the Walker. It is used to transform and rotate the Walker. If any of these things go wrong check that the Pivot is correctly assigned.

## Path Types

Among other base functions Walkers have a setting for PathType which specifies the kind of pathfinding it will use to get to its destination.

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-13T18:39:46.498Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;OBNLZ62Guk_9WiO55ID5\&quot; version=\&quot;14.1.9\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;LbbmEFd_tO8RjvzimPEi\&quot; name=\&quot;PathType\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

Check out the scenes in .../CityBuilderCore.Tests/Other/MovementPlayground for interactable examples!

### Road
Simple A* Pathfinding inside the road network on the map.
Usually used for all kinds of destination walkers.
> carriers delivering goods, workers walking to a monument site, ...

### RoadBlocked
Same as Road but points with RoadBlockers are removed.
Usually used for all kinds of roaming walkers.
> water carrier distributing out water, 

### Map
This Pathfinding uses Unity NavMesh. All demo scenes have a gameobject called Navigation that is used purely to generate the NavMesh. To change the NavMesh follow these steps.
* activate Navigation gameobject
* adjust the objects inside Navigation
  * make sure Navigation Area is correctly set to Walkable/Not Walkable
* bake the NavMesh
* deactivate Navigation gameobject  

If you want the walker to use a NavMeshAgent instead of strictly following the path you can assign one to the Agent field.(as seen in MovementPlaygroundMap test scene)

> immigrants walking to their new homes, hunters walking to pray, ...

### MapGrid
Simple A* pathfinding of all points on the map that are not occupied.
Only feasible for small maps, on larger maps use Map pathfinding instead.

## Path Tags

The Path Tag field on WalkerInfos can be used to pass any kind of Object along to Pathfinding. The following ways to use this are already built into CCBK.

### WalkerInfo
PathType: RoadBlocked

Either assign the WalkerInfo itself to the field or check the Path Tag Self checkbox to send the WalkerInfo itself to Pathfinding. By using the checkbox an additional Object can be assigned to the Path Tag field.  
For example the Three demo has RoadBlocker buildings with RoadBlockerComponent components that block off certain WalkerInfos that can be changed in a dialog window.

### Road
PathType: Road

By using a MultiRoadManager instead of the DefaultRoadManager and creating Networks for each Road it is possible to have multiple road networks that can even overlap. The Road object assigned to the walkers Path Tag then decides which network a walker can use. If the Path Tag is left empty in this scenario the walker can use any network.

The Urban Demo uses this for the Road and Rail Networks. The Urban Demo also has an example of road switching in an extra scene called Tunnel which demonstrated the RoadSwitcherComponent that can be used to switch walkers between different RoadNetworks. Keep in mind that the start- and endpoint has to be on the same network.

Multi roading is also demonstrated in the MultiRoadDebugging test scene. (/CityBuilderCore.Tests/City/Movements/MultiRoadDebugging.unity)

### Tile
PathType: MapGrid

The DefaultStructureManager has a field called PathOptions which can be used to define additional Pathfinding Networks on the Map. These Networks differ from the normal one either by only using certain GroundOptions(Tiles) or by restricting the level of structures that block it. The Tag on the path option has to match the one in the WalkerInfo for it to be used. This could technically be anything but one of the Tiles is probably intuitive.

Structure pathing is demonstrated in the StructurePathDebugging test scene. (Assets/SoftLeitner/CityBuilderCore.Tests/City/Movements/StructurePathDebugging.unity)

## Walker Modes
The walker base class includes helper methods for various modes of walking. These save their states automatically and can easily be continued on loading.
### Walk
Directly pass a WalkingPath for the Walker to follow it immediately.
>used when the path is checked before the walker is even spawned like storage walkers  

### TryWalk
Tells the walker to try to find a way to a target or give up after a certain time. The walker can be given a target building or position to check pathfinding by itself or a function that returns one.
>deliver walkers spawned by production are spawned and have to figure out a path afterwards

### Roaming
The walker randomly walks around while trying to avoid points already visited. It does for a set number of steps specified in Range, how many positions it remembers is defined in Memory.
>well workers handing out water, bazaar workers selling food

### Wander
Moves to a random adjacent point
>homeless walkers
  
## WalkerAction

These allow encapsulating the state and logic of an action a walker can take. A series of these actions can be started as a process on a walker which will then perform them in order. For example a lot of the tasks in the town demo use a WalkPointAction followed by some animated action like WaitAnimatedAction.

In the earlier demos(three, defense, urban) walkers were more or less single purpose so the actions they take are baked into the implementation of the walker. The newer town demo uses a single walker to perform a wide variety of actions which is why this higher level way of controlling them was created.

To create an action with new custom logic simply create a class that derives from WalkerAction. For a minimal example check out the WaitAction which simply waits for a set duration before letting the process continue(or finish if it's the last one).

The persistence of walker actions is a bit atypical for CCBK, instead of having some save method that returns their state they are directly serialized. This means that [Serializable] and [SerializeField] attributes have to be set up and fields that can't be directly serialized have to be converted using ISerializationCallbackReceiver. A simple example of this can be found in WalkBuildingAction which has a reference to a building which has to be turned into an id for serialization.