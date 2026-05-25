#work #cpvt #dailynote

## todo
- [ ] if we have no object id we dont need to create a path, check if object id is optional in sapient
- [ ] when moving forward in time check which messages to process in on_update_scene. If we have too many detections, destroy the oldest one
- [ ] when detections are older than 10 second remove
- [ ] when detections have previously destroyed paths, add path again ? Dont connect previous and current path, maybe store some index, which we can use in geometry nodes to determine which vertices to connect.
- [ ] when mobing back in time, destroy objects whose start frame are bigger than the current frame. If there is space, add older detections (provided they are not older than 10s)

- [ ] have an object info panel panel in the sapient panel. E.g. when the object was detected, or which edgenode is selected

## Server

- [x] Move \_edge_nodes and \edge_node_by_id to sapient_server (as well as the other blender stuff such as register and unregister)
- [x] When we get a message from the edge_node, directly call EdgeNodeEntity.handle_message, instead of relying on a pre_scene_update method. The handle_message shouldn't directly update locations, but rather use keyframes (see late)
- [ ]  Careful with set_currentdatetime in sapient_server, when start_time changes, all keyframes will be invalidated. Rather than change starttime, don't go beyond 1000000 frames ever. Never roll over time. Maybe store seconds or something in attributes, so we can always reset the keyframes
# visualizations - keyframes and geometry nodes

- [x] Use mesh for detections path, store first_frame in the vertex attributes, use geometry nodes to hide/show vertices
- [ ]  For the sphere detection, also use a geometry nodes modifier, change the color depending on age. (nice to have). Define a **lifetime** and **birthframe**.
- [ ] We do definitely have to limit the number of objects shown at one time I think, but how to recreate stuff? Well we do have the sapient messages stored internally. So we should be able to throw objects, and get them back later by reprocessing the sapient messages. First, run some benchmark and see when stuff becomes slow. 
	- [ ] Deleting stuff is easy, if we go over 100 e.g., just delete the oldest detection
- [ ] How about, we use a single object with instance on points for detections, then it probably doesn't get slow ever. How to create the relationship lines though... Check the gemini 
# Logger

- [ ] Check if the logger won't crash if it rolls over
- [ ] We have to write our edge_node_connections away at some point, or the blender memory would keep growing...

## Test

- [ ] test importing sapient logs
## other

- [x] when disabling entities, also hide collection.
- [ ] Think about what happens when detections are not received in chronological order, should we insert vertices? 
- [ ] what's the edge_node - custom edntry??
- [ ] we want to get report id when clicking detection, so instancing is not good idea