> [!lk-navbar]+ Navigation
> [[Home]]

# World Map
# Note

> [!hint] How to use this note
> I didn't include a map category because aside from the world map, which can be accessed here, regional or local maps can be simply imported and used in their respective `#Geography, #Country, #POI`, etc. note. The respective map image can be imported to Assets/Maps
> It just doesn't make sense to have them all be their own markdown note to me
> There are two methods i recommend for embedding your maps:
> 1. Using Leaflet Plugin
> 	- Pros: Allows you to pan and zoom the map while inside the map note itself
> 	- Cons: More restrictive in general
> 2. Using Excalidraw (and embedding into the note)
> 	- Pros: A lot more flexible with what you can do with it. You can stitch maps together, add text, import custom icons and markers, etc.
> 	- Cons: You can't interact with the map itself on the note (But better than a static image, as you can simply double click to open it)
> 3. Static Image
> 	- Pros: Simplest solution
> 	- Cons: You can’t connect points on the map to notes from your world

# Leaflet Map
```leaflet
### Tutorial: https://youtu.be/54EyMzJP5DU
### id must be unique
id: example-map
### Lock pins so they can't be moved
lock: true
### If true, view of map will recenter as you zoom out. 
recenter: true
### If true, disables mouse scroll for zomming in and out of a map. Button controls still work. 
noScrollZoom: true
image: [[example-map.jpg]]
### Map Pixel Height x 1 / (Pixels between Bar Scale / 100)
### Map Pixel Width x 1 / (Pixels between Bar Scale / 100) 
### Note that this formula requires adjustments depending on your map. The idea is to determine the number of units between your bar scale. We divide by 100 here because my bar scale measures in 100 units. If your maps scale bar measures in units of 50 them you should divide by 50 instead. The idea is to calculate how many pixels are equal to 1 unit. 
bounds: [[0,0], [1815.07, 2805.48]]
height: 100%
width: 100%
### This sets where the map starts by default. Set it to the middle (half) of your bounds. 
lat: 907.53
long: 1402.74
### 0 is no zoom. Negative zoom steps away from the map. Positive zoom steps towards the map. 
minZoom: -1.5
### Max zoom is 18. 
maxZoom: 1.5
### Hover mouse over the Reset Zoom icon to see your current zoom level. 
defaultZoom: -1
### How far it zooms in or out with each step. Can be in decimals. 
zoomDelta: 0.5
### This is a string so can be any text. Change it to match your maps measurement scale. 
unit: miles
scale: 1
darkMode: false
```

# Excalidraw (double click) 
![[example-map.excalidraw|70%]]