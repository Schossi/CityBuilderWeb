---
permalink: /manual/resources
title: "Resources"
sidebar:
  title: "Manual"
  nav: manual
---

The different resource systems deal with creating, moving and consuming items. Items are ScriptableObjects that specify how the item is visualized in storage and UI among other settings.
>wood, meat, clay, iron, ...

Items are stored in the ItemStorage class which can limit how many items they fit by item quantity, item units or stacks. ItemStorages are either part of building components or a global manager. ItemsStorages on Buildings can be set to global mode so their items go to global storage instead.
>gold is stored in global storage, food is stored in buildings

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-13T18:41:30.330Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;HViaGpXDFcwgwruZ2w7d\&quot; version=\&quot;14.1.9\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;3PMwnGwSntyarzqDvJic\&quot; name=\&quot;Resources\&quot;&gt;7Vxbc9o6EP41PCbjm4x5bICmTdM5TMiZlr6cMbYANcLy2CKB/vojYym+iCYiASwgL4m1FrK9u99eZbfs7nx5nfjx7DsJIW5ZRrhs2b2WZZm2Z7J/GWWVU4Dj5YRpgkI+qSAM0R/IiQanLlAI08pESgimKK4SAxJFMKAVmp8k5Kk6bUJw9aqxP+VXNArCMPAxlKb9QCGd5VQPlGZ/gWg6E1c2DX5m7ovJnJDO/JA8lUh2v2V3E0JofjRfdiHOmCf4Arp0ScBq9SWJH+LRjTW9v1ld5It93uYnz4+QwIi+eelf/7mjKV62b+xf8bc7EMN/2p0Liz8aXQl+wZCxjw9JQmdkSiIf9wvqVUIWUQizVQ02KubcEhIzosmIvyGlK64L/oISRprROeZn4RLRn6XjUbbUJeCj3pKvvB6sxCCiyepneVD6VTYsfrYeFb8LP2VaxIZjTIKH+xmKcvJnhMUNKfKXyyEliySALzDV5mruJ1NIX5jXyedlHC/pKpfeNSRzyJ6ETUgg9il6rCq0z3ExfZ5XyJ4dcPFvoQr8rh99vOBX6kHMrpot7WL2HFfjhB1Ns6MfPn6Aiaw7GDNYZzryNEMUDmN/zacnZlmqGuCncY71CVpmmnQ1YcLoEkyS9UL2ZALdIGD0lCbkAZbOhO3O2DC2lhl7DAqXL3KZn7UcDndu7+w2yMdPhfVw+ZRZyXAI2s7l4pw6RHeMvo4i+oBW6BNa14yYC9GOSmdeEbO5nZhTJhG6yRavT5SscclkRySCFWudLTQhEeVPZO5Bf4Ci/piOVgrknrydqCgQ14yy7ii7e00UCOilQEDy/0NKkiy6ltx/l8xjxn/GrbrKFQplvh4F1Jx+6ENvstHpu4EHxxMhOX411ah46wjAsUAtAmhfyjGAtyEGAGBf4D4WbO8YSp4ilGytkORJSBokJFwEFJFIIzDtCz+dWgAtKgFNgacjiePrVwrndzCAWXojsZ3l+XF2OINLnyGGcSqGCWL3ApOCOhAkS0U0LMkRDufd/kddELZVk0RHTRL2vlIZ84jKDc3HEQI3u7Nq/KcDgjJr87eM1zGcSw+0TcfK/3aqC+bGmK9RU4jnm3pHGeKIdGQHcazGiZAtyrWvZkI7V9T3WRlDMvjM/WF4rv63+fDVbjeB6b3h7K0VkLdUW3aNaVVIm1pB2vY+nIImTsE9Tg0St1POAlgSkN6x1RFcpwHn5hgcp3HH4JgSbw/tGHZZSNSkA2KqtkA0K2GL26ln6tfnlaYDVw2Ve0vTHbtJbytc6lbe9j29KI1bCaZqL8HSqwJqys2EHmIOD40X55mEAWA17msbLawcHNUax9Dq/lmvPQqmXEkfsEed+emGHuEpbxEy6+CW6+qH3SLUaO//w2HLfvh1h93WCtqWvPtvmG2hPSdYX2gHa/ABa01g3VaFtV57esV9b+h9oxhtCrdPJqu+MHVLqy05fOo/EnwuGdGFVRdI8zmRfV6bJjXOiWzVwEl0pTWxsOJ2FJvNZxQ+Nf7ihC3HtNcwgol/Lga37gF12AnQ+TC4mhhc1dKy6PjqYnDl0vI6pE17iNnGKD3lThFDdHVruuPKKWrnkDGtUI56W102ry802s/IKTpOw04RHF8XoGRzRxWTe9w1BUe1C+BpZX8dOYs90+301gbje9CCgttsffAt74zWsGyeCJbFq3zHtuPGld33df9+o1bd+mOIa34XoyljdS9gTMzAfJVhCQU+/sRPzFEY5koHU/THH6/Xy9gfZ28PrB8GXLVAT0lAL0JAQvHzB0X4VVvlb3Zs9NTGpet1uHF76xsVYgqZTFK4l9cj3Ea2Ur8rgTrRnoAy5h29egKu/Hri8N/B4HZ0TLAXfY1dwN6xDKA97Butm1RdvaEG+xMN25Vhrxfq2/JLUf3vg/ujAr3IPHYCekfYQR7Ni09h6WsDgLw9+q9faDjhkgo43Aea2LD4vFsuxuIjeXb/fw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

The two essential interfaces regarding resources are IItemReceiver and IItemGiver.  
* Item receivers are building component that accept items from others.  
Other components deliver items to receivers.  
* Item givers are building components that provide certain items for others.  
Other components acquire items from givers.  

### Storage

Storage Components act as both receivers and givers. They need a StorageOrder for every Item they store. Storage components performs actions in the following order.
* get items with StorageOrderMode GET from other givers
* supply receivers with a higher priority with items(production)
* empty items with StorageOrderMode EMPTY to other receivers

>silos, storage yards, ...

### Production

As long as it is supplied with items specified in ItemsConsumers a production component will periodically use up those and produce the items specified in ItemsProducers. It does not actively get the consumer items but instead registers as an IItemsReceiver. It does however spawn delivery walkers to move produced items to other receivers.

>barley farm, brewery, clay pit, potter, ...

### Distribution

These components send out roaming Sale Walkers that take note of the items IItemRecipients it passes need. They then look for IItemGivers that give out those items and send Purchase Walkers to get them. The Sale Walkers are filled up with items whenever they leave and pass out the items to the IItemRecipient they pass.

>markets

### Retrieval

Retrieval Components periodically send out walkers that get items from the closest dispenser. They then spawn delivery walkers that try to move them to an items receiver.

>hunting lodge, wood cutter, ...

### Collection

Collection Components spawn walkers that collect items from generation components the pass while roaming. These also use delivery walkers to move the collected items on.

>tax collector