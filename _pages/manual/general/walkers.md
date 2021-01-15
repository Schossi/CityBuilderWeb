---
permalink: /manual/walkers
title: "Walkers"
sidebar:
  title: "Manual"
  nav: manual
---

The primary way to move things about in CCBK.
> storage workers moving items, hunters collecting meat, architects inspecting buildings

Among other base functions Walkers have a setting for PathType which specifies the kind of pathfinding it will use to get to its destination.

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-13T18:39:46.498Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;OBNLZ62Guk_9WiO55ID5\&quot; version=\&quot;14.1.9\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;LbbmEFd_tO8RjvzimPEi\&quot; name=\&quot;PathType\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

## Walker Modes
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