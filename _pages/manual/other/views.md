---
permalink: /manual/views
title: "Views"
sidebar:
  title: "Manual"
  nav: manual
---

Views can be used to alter the way the world looks and for presenting additional information to the player. In the Three and Urban Demos they are activated and deactivated in the UI using a ViewActivator. In the Defense Demo only one View exists that is always supposed to be active so it is assigned as the DefaultView in the DefaultViewManager.  

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-12-29T16:22:17.508Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36\&quot; etag=\&quot;9NNb2d56QiBZid5XVfDS\&quot; version=\&quot;16.1.0\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;li4_7FCLNsZ3qGiNTv1N\&quot; name=\&quot;Views\&quot;&gt;7Vvfc5s4EP5r/NgOSIDxY+Pkrp1p5m7qmyZ56siwBlqBfLKI7fvrT4AwP924dwYlcWb8gFZCEvvttyut5Amex7vfOVmHt8wHOkGGv5vg6wlCpoXQJPsZ/r6QTGdOIQh45KtGlWAR/QNKaChpGvmwaTQUjFERrZtCjyUJeKIhI5yzbbPZitHmqGsSQEew8AjtSu8iX4SF1LWNSv4RoiAsRzYNVROTsrESbELis21NhG8meM4ZE8VTvJsDzZRX6sW9//Zld5ss/vy+xTsbeyn9+vCu6Oy3X3nl8AkcEnHermfq08S+1Bf4Un2qyLgIWcASQm8q6RVnaeJD1qshS1Wbz4ytpdCUwu8gxF7ZAkkFk6JQxFTVwi4S99nr721VeqjVXO9Uz3lhXxYSwff39cJD1UNWrF7LS+V7xfdlH9Uyhyd0qdptWMo9+Ek7xQ5BeAA/6885GIxkGrAY5CTlexwoEdFjc3JEmXxwaFfBKh8Usr9iQMYbzOPA7OqEWU3ykdBUjXQNK0g28DWC7QQ5VM78asnlUyBynRWSqC1YMamzurU4f6esrHi3yfH+IBuYxnpXVZa9ZIPNWbxmm0hA2aX8nqLX5khSXBu9ZaI1U1pFlM4ZZTyvwT4Bd+VJ+UZw9gNqNY7nwnJ16O0RuIDdfzCJLoRlL47ikgqHJlblbRVczJJvYS2wlAHn/OTGOslt1qhdEf285M4sR03EHIPszolkN4+Yyjhst9DLc+oV1A8NpF8W7kirl3eOefmrNKJ+lAQfgVDpisb0982hrwh/dX4ftfw+Mnr8vj2q37fe/P55+e+e6veRTv67x/h/R+gP4BrYXx/4IrjvaOe++VQQqOEwuA2UY34BTwyHvw2ub/Xh76IldpwB8bfsZ+f7j271Ci6OiX4x4sVgr5/702PYS+E1xKyjWKkS0YziTT0mLIGW0pWI0ChIZNGTKgQpv8oUHHmEflAVceT7+cJiG8rd/mJN8gC75WTdWWzUo/mQiOFpa4dunbhDx4Mh5upcqWlMvz2dVjNOXHIh9P9sY6Q866Wm088ItPUSgMZac25jAN3vrQdMsJ9qIFjr5qucZi343hEZGt8y7GeL3+0Mu3Vq/B5sxYW7Ky4d9B+dkuhUSmo93Cyn2abkPKVUbkrHZWVzzFfDyXYGxDZ174Kw1qXWa8x+liuvp+mu95Db6qf7Z7KH8ZIeGdkbI75eqk91Ux11w+9fIYe3dEdvuuOQsNKW7kDdE4pPxeFARpcWWDxk8TLdHFHpcYasVivk9TLEd5aOPaTG0cxuaBz3XAFxexTuDhYLu6cBuUvUcQaQ37z0LyET7PTd/Bl3DXRRJ8BjbHnwyVsevVd/XmD66Xlf/TkZeMvQCXw5TZ2evn7fZwH8MfLgEg79n4G77978+nRLomROYuBkzJVVPzuHD7m2MX1vd1CY9YFgDwVCz+L2D/nllOxvSUKCcZe42oBwtANRZoXbrlC5pNHcYWu88/o/MOWCd9pnAjNnismgu5yW/5sOeOlFFqu/UeV1tT+j4Zt/AQ==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>


Views are ScriptableObjects which are found in the ContextMenu > CityBuilder-Views-...  
The following Views are included in CCBK.  

* Composite  
Placeholder for multiple other Views(only one view is active at a time in IViewsManager) 
* Culling  
Applies a LayerMask to the main camera
* Layer  
Visualizes the values of a layer on the map using IOverlayManager
* Connection  
Visualizes the values of a connection on the map using IOverlayManager
* Efficiency  
Visualizes the efficiency of Buildings map using IOverlayManager
* BuildingBars  
Visualizes an IBuildingValue by adding a BuildingValueBar for appropriate Buildings using IBarManager
* WalkerBars  
Visualizes an IWalkerValue by adding a WalkerValueBar for appropriate Walkers using IBarManager

To create your own View just derive from View and override the Activate and Deactivate Methods.

## Values

IBuildingValue and IWalkerValue are used to query Builders and and Walkers for certain numbers. For example the implementation of IWalkerValue on the Item ScriptableObject returns the item quantity that the pertaining walker carries. Most Values are implemented in ScriptableObjects(Risks, Services, Items, ...). A good Example for a Value that is implemented on the View instead is the IHealther Interface.  

## Bars
Bars initiated by the Building-/WalkerBars Views and managed by the IBarManager are the visual representation of a IBuildingValue or IWalkerValue. They are not specific to a certain Value but rather just translate the number returned by the Value to a viewable form. When a BarView is activated the IBarManager instantiates Bars in all the appropriate entities.  
Creating a new Bar is done by deriving from BuildingValueBar or WalkerValueBar. These base classes provide all the necessary Methods to get the Values(HasValue, GetMaximum, GetValue, ....)
