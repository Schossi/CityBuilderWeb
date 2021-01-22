---
permalink: /manual/dependencies
title: "Dependencies"
sidebar:
  title: "Manual"
  nav: manual
---

Dependencies in CCBK are used similarly to IOC Containers in other areas of development. The implementation however is stripped down to a minimum to acommodate the performance needs of games.  
Basically Dependencies allow the registration and retrieval of interfaces. This allows the implementation to be changed and moved wihout having to rewire all entities that depend on it.  

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-22T12:44:23.235Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;xl_U9JJmQqgsUgsOQ9Im\&quot; version=\&quot;14.2.4\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;uRjRt3pyHetSKXoSinp3\&quot; name=\&quot;Dependencies\&quot;&gt;7Vrfd6I6EP5rfKwHCCA+rtrtem67p6eee9vuy54IQbKNhBNi1f3rb6JBfmqrrWBbn2SGMIT55ptMJrZAf7q4YjAKbqiHSMvQvEULDFqGodsdIH6kZrnWdIG5VkwY9tSgVDHCf5FSako7wx6KcwM5pYTjKK90aRgil+d0kDE6zw/zKcm/NYITVFKMXEjK2nvs8WCtdSwt1f9AeBIkb9Y1dWcKk8FKEQfQo/OMCly2QJ9RytdX00UfEem8xC/s7uH6P94f9vjo5+LxH/fRGroXa2Pf93lk8wkMhfydTSvbMV8mDkOe8J8SKeMBndAQkstU22N0FnpImtWElI65pjQSSl0o/yDOlyoY4IxToQr4lKi7aIH5Q+b6UZpqW0oaLJTllbBMhJCz5UNWyDwlxfSxlZQ859OQq4nojpDX3ys/shAfLzg3cRSdMRftGKfYwSGboF327E0ECeohOkVi0uI5hgjk+Dk/Oag4MNmMS3EWFwrqfWA3zrA3A3unUdjBGfZmYHcahd08w94M7N0mYVeTfIZkpt40QD6cET7kaHoDQ1H5sFJgpLBL3OYB5mgUwZUz5qJAzENc7fZnxDhaHOD4sqOUla6qwFQJagAlz9OCblOlBZliztHe7tr+09z/NR4GN7/+/T3Su+A+Xv68aJRQgg5WjlPdF0glhFvEsPh0AXiBaPppE80qE60SEOONRFs9+o0xuMwMiCgOeZyxfCsVmbAEIBeXpqMVImttMY2zzdQODz3rHHqnFXrgFELPNmoIPae0oFwJz1SF4zUcI5IPIUjwJBTXrkBHxkJPLhNY7NO/qRtT7HnraEUx/gvHK3sSeOULYdzqtazBPuuOaiooY63NIpENku0s27oeXWjtjq1bOQSSuNoP9xTYZAj1/Vh59fvB8O0K6Fw9ECGRGEIXo7iMIyE4iiUgcQAjqXQJnXmnUxV0QKEs0MtlAehUlAW68Q51QfWEux+v0m5rnXwiNl9IxCupmNXrzs72KyvwLUSupwK3S4wbXhE6hmTEKZN9y2KwJEwL0AKKGJDJL+Nnpd243ngFF/ECJU3ZOrkJCiW73qko2c0KbppHo6Z9pmY91Ox8BGp2KqgpXspuIQ98LEAvb40/LTkr99P1krNzJmc95HQ+AjnLG43hHXLRl+Wn0zg/nTM/6+FntyZ+HtR1sJ18YAK7cOT8wnjDcgqh+LYuRaVnks1dJnvcoQmOeUXK+Gi9ih3k3JpNZM+u2KtQzaNDexXJxK22WTBs6G3NyNs5XkOjW14m5NFGPMBxhMIYsW2HHJ92pQBm0ytF8mHZLpPgHsPjGcfC1YZNxBR6YwGKPZFXfTqNaCidUETpTUdRPiakTwllK1vAg8jxXdnL4ow+ocwd23XQ2D8iRkYhCZpWGSO96vTKPtbpVTlBDhCRxdWyDM89JE/vfUxYwMb3fcOtxMazx7Zl14iN1W0am0a7FEk1tVehdTrHONtPBl9RUBlbIuXddzy7Zvkl2xGmWUiQdo2LWCUajXYjPiMJQZmE21empjgIyhz8Sl2HIg1t7Xg0FGL6v+n1diD99zm4/B8=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

Most systems in CCBK have some central manager component that all the components need access to. Theses managers are not wired up in the editor or implemented as singletons.  
Instead the system includes an interface for that manager. The Behaviour that actually implements the interface calls Register on Dependencies when it awakens in the scene. Any components that need the manager call Get on Dependencies.  

When possible keep changes to CCBK to a minimum. Instead remove the default implementation from the scene and add your own.  

Let's say you wanted to change how the production components are prioritized for delivered raw materials.
* copy DefaultItemManager to the project folder and it to something like MyProjectItemManager
* change the code to fit your project
* replace the item manager in the scene
  * pro tip: switch to debug mode in the inspector and replace the script to keep the field values

Many of the default managers register multiple interfaces for convenience, these can be easily split up thanks to the Dependency system. To replace just one of those interfaces with a custom implementation comment out the line in Awake where that interface is registered. That change will be lost if the Asset is upgraded but should be easy enough to restore.  

Dependencies are automatically cleared between scenes.  

All interfaces registered with Dependencies are effectively singletons. A possible extension of the system would be passing a tag when registering and getting to partition different areas of dependencies(eg different road managers for underground, ground and sky). CCBK does not include such an extension to keep performance optimal for those that do not need it.