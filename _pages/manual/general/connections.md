---
permalink: /manual/connections
title: "Connections"
sidebar:
  title: "Manual"
  nav: manual
---

Connections define networks of values made up of feeders, passers and consumers.  
>water that spreads through pipes or the reach of services through roads

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2024-08-19T18:01:29.714Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36\&quot; etag=\&quot;gBiD0NUX2TOLD0TWVbbh\&quot; version=\&quot;20.8.13\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;FSDSQPLhZI_XOnql79Xr\&quot; name=\&quot;Connections\&quot;&gt;1Zzbc5pAFIf/Gh4zAyy3vsbEppdkMrGtk0eE5TJdWQewav/6QgAve8xMOiLn8CQeLuLHGfl+u6rGJsvt59xfJY8y5EIz9XCrsTvNNA3ddauHurJrKrbHmkKcp2G70aEwS//ybs+2uk5DXpxsWEopynR1WgxklvGgPKn5eS43p5tFUpy+6sqPOSjMAl/A6jwNy6SperZ+qD/wNE66Vzb0ds3S7zZuC0Xih3JzVGL3GpvkUpbN0nI74aKG13Fp9pu+s3Z/YjnPyo/s8O1u+zrbeT/dZ3t+o+8e44cH58ZqjvLHF+v2DbcnW+46ArlcZyGvD6Jr7HaTpCWfrfygXruprnlVS8qlqJ4Z1WJ7OJ6XfPvueRr7d1+1DZdLXua7apPtHmGzS9sxJmufbw78O/zJEfqu5rdXPN4f+QClWmi5/AcjZhCE5FCDZNKDZJLrJAYgscsoRakQEylk/rYvC23uhVZVL8pc/uZHazxzwRynJ67kmo/gxxgj13w2QUjkOsmhB8ki10kuQUjkOsmjBwmolYcN6ROAZPV6Q4y8gAfBuRviwrMtW7+SjWFztfRrc40i8zzX0Fk4dl+iQa1fLRgFRsmVXL/C9NCvGA/DFTgfOlcYOC68C6EEDqCJ6Fxh4NBHyBWYJTpXghkFmCU6JIIZRTVLhq3fFsGMomoiPiSCGUV1PnxIMKOM0U1U50Pn2h2YUvOpAocPieDcg2pj+JBgekCHpKoVPiQYBfAhkeskghMJQK2w/dMmKOlArdAhQUk3LqOEM9VHrvmg11/YfTRsDJ0rjAL99ivOCBw+V5ge+h0pGogrtX7tzmfkXIEmonMlGDiAJqJDIhg4VE20sF3aIRg4VE3Eh0QwcKjOhw+JYOBQBQ4fEsFZAdXG8CERnBVQ1QofEsFZAdWT8CFBr8eHRK2TXIJD/KonGdgy6RI0btWT8CFB4x5j3FPVCp8rlPRRciXXr9f+ghDOcBo+VxgF+uWK84U2fK4E04PqfPiQCKYH1fmGhFT8+P7Cv26+iIzPn1w249nT/AbazJTzkOea6YjqtW8X9VJcL/1628TUq49KHa598bO4XlsfbOoLIaOoWup5TmKQXwfYH7hE+58ND3KNoEw9+0VRX6PR3aFUuOe+nTksXGhUE5kV62XPeIe5Ual4zw29D4uX4IApiJQD5u6zjAiOl4JEic2IoPCAdIjNiKDvgKSHzYjgYClIbdiMCI6VggSGzai7ZpQggQSGDongWClIYNeDVD09/F/Q27qjf11i9/8A&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

Similar to layers, types of connections are defined by creating a Connection asset from RMB/Create/CityBuilder/Connection. The Connection asset has Layer, Layer Range and Layer Falloff fields which allow the connection to act as a LayerAffector. The __Urban Demo__ uses this for a water layer that spreads out from the connection. It also has a power connection that is directly used without a layer. For another simple example of connections check out the __ConnectionPlayground__ in the CityBuilderCore.Tests folder.

## Passers

The the most basic piece of a connection, theirs points pass on values and both feeders and consumers are just variants of passers. A __ConnectionPasserStructure__ is used in the ConnectionPlayground to spread a connection through a road network(found by key). The same component also spreads power and water through StructureTiles in the urban demo. The houses in the urban demo have a __ConnectionPasserComponent__ that spreads power through the buildings.

## Consumers

Consumers are special passers that only receive value but don't actually pass them further. In the ConnectionPlayground this is used so that only buildings directly connected to the road receive connection but not buildings that connect to them. They use a __ConnectionPasserComponent__ for this with the IsConsumer field checked.

## Feeders

Feeders are where values within connections spread out from. Both the urban demo and the playground use the __ConnectionFeederComponent__ on buildings(pump, power station) but other components to feed from structures or tiles are also available. The feeder component has fields for the max value in the points of the feeder and the range and falloff in the connected passers.  