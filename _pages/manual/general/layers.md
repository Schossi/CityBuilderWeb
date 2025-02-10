---
permalink: /manual/layers
title: "Layers"
sidebar:
  title: "Manual"
  nav: manual
---

[Layers](https://citybuilderapi.softleitner.com/class_city_builder_core_1_1_layer.html) define numeric values for every point on the map.  
>resources like water and ore, desirability of buildings or even the spreading heat from fires

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-14T18:10:25.818Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;2_rCSNjhgQGL04RxDDe4\&quot; version=\&quot;14.2.2\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;lwmNovz0qtnE8QjUyyNz\&quot; name=\&quot;Layers\&quot;&gt;7ZpNj9owEIZ/TY4rJTGEcCwUumrVS6lKr97E+VBNTI1ZoL++DiSQeIrUCqEZVl1xMK8/8D62Xs848dh0tf+g+br4rFIhvdBP9x5774VhMAhDr/746eGkjMaDk5DrMm0aXYRF+Us0ot+o2zIVm15Do5Q05bovJqqqRGJ6Gtda7frNMiX7v7rmuQDCIuESqssyNcVJjYf+RX8WZV60vxz4Tc2Kt40bYVPwVO06Ept5bKqVMqfSaj8VsobXcjn1m1+pPU9Mi8r8TYfncK0+/owL/fpp/OQH7Ptwlz01o7xyuRX92ZpDi0CrbZWKehTfY5NdURqxWPOkrt3ZRbdaYVbSfgtssRlPaCP2VycanP99u2+EWgmjD7ZJ26GF22wZ1u6F3WUBzpiLDvy2H2/WPD8PfcFiCw2Zf6AUEqQUkqPECFJi5CgNCFIakKM0JEgJ+FKETSkiSAn4EjqlEUFKwJfQKcUEKQFfQqc0BpSG6JRcXxqgu3c7gQ4mdEquLxGgBINv/M1EEBOMvvExuf5NABMMv/ExuQZOABOMv4MbD7qslHKqpNLHvizlIs4Sq2+MVj9EpyZKYvGS3cn00Y/GAMbsD0kWOCA+WRjnPyRZYJr4ZGFu8JBkgc/ik4X5xJIboa30tbRgw0jaKUxerBDldenbsWHo1/zdui+8yuu6esA5l1JlmS3deLyhLFQU9BeKxegLBVMa/MTPPd2GQ2xMLZQOpggdk3tUEcAEcxp8TO65QwATzGnwMbmHCAFMFB8puN4U+eiYYE6Dv5tcbyKACSYo8W2YnBAieOGBCP8UQvh+NHs3r3uoynT07Ph3H5cjABzmLfj70nU5AphgEoJ/cwNcDv8wgBkFOiVgcviUYDjf3jP/59R9WQHG8wQ4AQ/H5wQDegKcgInjc4IR/UPeJLm+P0I/HhlMAh6SrOuBBMi+kWchrmsSIPtGnoW4PkuALAyWl6duk20p07LKr18tx9dvli2Gzs3yjYElqbTQvXGOwvstof16eZ/5WNd5K5zNfgM=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

At the start of the game a layers base values are calculated using predefined tiles. After that LayerAffecters can register with the layer system to add their own values.

Here are some of the ways Layers interact with other systems
* requirement for building or evolution
>wells need a minimum amount of water, housing needs desirability to evolve
* (working-)affecter on building
>eg gardens affecting desirability, working stages affect entertainment
*  layer efficiency component affecting building efficiency
>fertility on farm buildings, 
*  multiplier for risk increase and service decrease
>fires happen faster in hotter positions and more water is consumed




