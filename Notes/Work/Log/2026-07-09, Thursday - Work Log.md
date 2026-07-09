#work
## To Do

- [ ] Determine how to implement Line Radius and Path stride in a flexible way that allows the user to easily adjust it (similar to object scale maybe).
- [ ] Replace all subscriptions with the new event system, which gives us more control, e.g. over what properties should be called in the UI. When we use our custom FloatProperty e.g. it is sometimes difficult to give a specific name and description. The event system is way easier, and can be used more broadly.
## Wrap-Up

## Brain Dump 

### Geometry Node inputs

when updating inputs, we need to perform interface update on the node group, e.g. modifier.node_group.interface_update(context). How to distinguish between global and local settings then? I guess we loop through all objects that have a modifier with proper node group on them.. if they have a local setting override, use that instead.

So for object scale, Have it be a geometry node input maybe?

### Object Scale

Store a custom "CPVTObjectScale" bool property, when true, the object will be scaled by global scale, if false, a local override is used, which can be reset by an operator in the settings.

A global cpvt scale is stored in the scene, when updated, update the scale of stuff. 
### Event System

Maybe make a simple subscription system, describe events by string, then just say 
subscribe_to_event("cpvt_scale_changed", func...). in other parts, we can do stuff like emit_event("update_cpvt_object_scale", force, ...). 

small downside is that it is not super obvious which arguments will be provided when an event is emitted, but just document this somewhere. When subscribing to an event, always provide default arguments, so we don't crash. 
### Make a lot more use of depsgraph update handler

In stead of creating a callback, just update whatever needs to be updated when the depsgraph update post is triggered. If we're careful to avoid unnecessary calculations, this should work...
Maybe use object scale as a demonstration. we'd have to tie an 'update' function to every object though, maybe this is a bit much. 
### Global vs Local settings

We should have global settings that we can override locally:
in global settings add a button to force setting to all (erasing local settings)
in local settings, add a checkbox to override global settings. Have a local and a global tab in the visualization panel.

This would be helpful for the color of sensors as well, which was actually a requested feature.

We can store the LineRadius in objects as a custom property I guess.

### SAPIENT Detections as Entities

Should SAPIENT detections be entities as well? Probably not, would overflow our UI. Still, would be nice to have a local setting, such as line radius for objects.