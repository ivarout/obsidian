## Deleting detection objects
Try to keep detection object with long paths around. Delete smaller ones with no path for sure. Hence **even if detection with path is older than one without, destroy the former.**

Store a list of deleted objects by **last frame seen**(or last time), but also by **first frame seen** so we can quickly search for any that should appear when moving back in time.

If an object appears again, rebuild it (including path) and remove from deleted objects buffer

When moving to any frame, whether forward or backward. Check if there are any entities in deleted objects that should be shown the current frame. Rebuild it if so.

~~When importing a sapient log. Store everything as deleted object, build when necessary.~~ Ooor, just check how many object-ids are in detections. Then sort them by length, startjng at shortesr path length, delete those not in current frame.

Instead of deleted object, maybe call is **archived detections**.

Yappari, have server call **Entity.handle_message**. 

We probably o ly need to do all this stuff for locations, not **directions**. For directions we just have a fixed number of objects I guess. Ah well, not for now, later. 

We also have to think about status messages, but we dont have too many edge nodes, so no worries, just use keyframes here.

- **max blender objects per edgenode** will mostly just use keyframes. Old object will be deleted. 

## EdgeNodeConnection no need to return messages
The edge node messages doesnt necessarily need to return messages, since we dont rlly use them directly in sapient server. Rather, the entity implements the most recwnt messages in its on_update_scene method. **make it an option to return messages**. 

## Store detection messages per object-id in EdgeNodeConnection
Such that we can quickly get all detections for one specicif object.

When going forward in time put reached max number of objects we want the oldest detection object. Just look at all detection object that are active, and delete the oldest
# (Un)Handle message triggered by on_update_scene
This will allow us to keep the number of objects limited to some max. When going forward in time we delete oldest detections

## One more time, who does what
- edge node connections receives and stores messages in realtime.
- entiry stores messages in archive where can can quickly query nodes by start or end frame (or time) in a sorteddict
- handle message just simply adds what is needed, add objects always, with keyframes, or actually, have an **immediate** option. Which will immediately add the object, and otherwise store it in archive. Maybe it should always just be stored in archive.
- When we jump to some frame, we check which detections should be shown in the current frame, rebuild objects that are not in the collection. Note we want to rebuild the entire detection path. So we want tk get all locations from the archive by object id as well
- objects not in the current frame are removed. Those in the past and of smallest path length are to be removed first. 

## On frame update
- only when jumping more than one frame do we have to take special action
- check if we have detections in the archive that we need ro show. Build the object, including its entire path, and delete an object on the past, with the smallest path length. That's all no?
- to check if a detection is in range, get set of object whose end frame is bigger than current, then get set whose start frame is smaller than current, then get intersect.
