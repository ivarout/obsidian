---

kanban-plugin: board

---

## Could Do



## Should Do

- [ ] Use Geometry Nodes for any type of visualization, lines to target are also perfectly doable!


## Must Do

- [ ] Use Geometry Nodes for Ground Point (See .blend example i made)
- [ ] going back in time with 2d coverage following drone, still not entirely fixed, or is it just a resolution thingy?
- [ ] Insert keyframe, check logic on when to add keyframe, get_keyframes_location didn't like it if there are more keyframes for x than e.g. z
- [ ] Use Geometry Nodes for Ground projection along entire path
- [ ] Fix 2d coverage plane altitude. Altitude is not set immediately when adding.
- [ ] SAPIENT import edge nodes never get a name
- [ ] SAPIENT we get lots of drone objects, maybe purge every now and then?


## In Progress

- [ ] Update Path to use same implementation as sapient paths
	- [ ] store distance since start as vertex attribute
	- [ ] Have projection to ground, at least at start and end point, and fixed interval in location (or maybe time)
	- [ ] Use to common click map operator


## Done

- [ ] Update to Blender 5.1
	- [x] fcurve access has changes
	- [x] get/set on Preferences doesn't work the same (e.g. when setting database folder)




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false,false]}
```
%%