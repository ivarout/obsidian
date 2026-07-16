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
- [ ] global target parameter logic too complicated, with locking etc. Should make this easier
- [ ] Defer subscriptions to Subscribable property. or have the option at least.


## Must Do

- [ ] have refresh function that recalculates height wrt ground vertex attribute for paths
- [ ] going back in time with 2d coverage following drone, still not entirely fixed, or is it just a resolution thingy?
- [ ] [[Path Visualization]]
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
- [ ] Make Global visualization settings more centralized, have local override options
- [ ] Use days and seconds since 1970-01-01 for time everywhere. Maybe we can still store a simple string, and just have set_transform or something.
- [ ] Create new way to log events to a file (such as DetectingEntityEvent). Maybe we should store the logging in the event class? by adding a log function. If not present, just create a json from the present attributes


## In Progress

- [ ] Remove old Event System. Instead create optional log function for new EventContext class.
	- [ ] detecting effecting events.
	- [ ] make distinction between ui and occurence events (check gemini for a good name)
- [ ] Update to Blender 5.2
	- [x] fcurve access has changes
	- [ ] keyframe access in path length should be updated
	- [x] get/set on Preferences doesn't work the same (e.g. when setting database folder)
	- [x] Setting geometry node modifier inputs has changed.
- [ ] Replace custom properties with new event system. This is simpler, and allows us to defer complex operations -> safer.


## Done





%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false,false]}
```
%%