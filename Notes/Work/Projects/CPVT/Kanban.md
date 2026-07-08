---

kanban-plugin: board

---

## Could Do

- [ ] Have option to calculate obscuration only when transform has been completed, to make it easier to move stuff around.
- [ ] Have emission strength reduced for vertices along path that are older.
- [ ] Add smoothing to path curve in geometry node
- [ ] Fix the jaggedness when playing animation (blender using temporal anti-aliasing)


## Should Do

- [ ] Use Geometry Nodes for any type of visualization, lines to target are also perfectly doable!
- [ ] Clean up big .blend files from repository
- [ ] fixed wing representation
- [ ] Simple RF jammer model
- [ ] Enable bloom (use compositor) in distribution package


## Must Do

- [ ] have refresh function that recalculates height wrt ground vertex attribute for paths
- [ ] going back in time with 2d coverage following drone, still not entirely fixed, or is it just a resolution thingy?
- [ ] Insert keyframe, check logic on when to add keyframe, get_keyframes_location didn't like it if there are more keyframes for x than e.g. z
- [ ] Fix 2d coverage plane altitude. Altitude is not set immediately when adding.
- [ ] SAPIENT import edge nodes never get a name
- [ ] SAPIENT we get lots of drone objects, maybe purge every now and then?
- [ ] Line to target visualization
- [ ] <details>
	<summary>bug when changing playback speed (maybe cuz I'm working in very messy file?)</summary>
	Traceback (most recent call last):
	  File "C:\Users\outi\AppData\Roaming\Blender Foundation\Blender\5.2\extensions\vscode_development\cpvt\util\log_utils.py", line 95, in wrapper
	    raise err
	  File "C:\Users\outi\AppData\Roaming\Blender Foundation\Blender\5.2\extensions\vscode_development\cpvt\util\log_utils.py", line 70, in wrapper
	    res = func(*args, **kwargs)
	  File "C:\Users\outi\AppData\Roaming\Blender Foundation\Blender\5.2\extensions\vscode_development\cpvt\scene\components\path\bpy_types.py", line 586, in on_update_path_visibility
	    for ent in scene.cpvt_entities:
	               ^^^^^^^^^^^^^^^^^^^
	ReferenceError: StructRNA of type Scene has been removed
	<details>
- [ ] Have test framework


## In Progress

- [ ] Use Geometry Nodes for Ground projection along entire path, both sapient paths, and user defined paths.
	- [ ] store previous position as attribute, so we don't calculate ground projection every frame for every vertex, only those not yet calculated
	- [ ] store birth frame so we know when to show stuff.
	- [ ] have refresh function, in case terrain is updated we need to update the ground projections too.
- [ ] Update Path to use same implementation as sapient paths
	- [ ] store distance since start as vertex attribute
	- [ ] Have projection to ground, at least at start and end point, and fixed interval in location (or maybe time)
	- [ ] (optional) Use to common click map operator


## Done

- [ ] Update to Blender 5.2
	- [x] fcurve access has changes
	- [x] get/set on Preferences doesn't work the same (e.g. when setting database folder)
	- [x] Setting geometry node modifier inputs has changed.




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false,false]}
```
%%