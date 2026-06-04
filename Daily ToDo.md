---

kanban-plugin: board

---

## Random Ideas

- [ ] store day (int) and seconds (float) in vertices of path. In geometry nodes modifier, calculate day and seconds based on current frame and scene start time, and compare if vertex is visible.
	
	Allow setting time zone in time settings


## 

- [ ] Check if changing interpolation type of paths still works (for both location and rotation)
- [ ] Fix deprecated fcurves
	
	Do we really need 'get_keyframe_data'? in path, can't we just store locations locally, which is probably way more efficient?
- [ ] Check all setters/getters
- [ ] Create all geometry nodes from python
- [ ] Add descriptive socket ID's for sockets in geometry node
- [ ] Add way to check if animation data (simulation zone) is stale/outdated.
- [ ] Allow Timezone


## Check

- [ ] instead of keyframes, use geometry nodes for paths, just like in sapient path
	- store distance from start as vertex attribute as well.




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false]}
```
%%