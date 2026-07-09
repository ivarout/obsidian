#work
## To Do

- [ ] Determine how to implement Line Radius and Path stride in a flexible way that allows the user to easily adjust it (similar to object scale maybe).
## Wrap-Up


## Brain Dump

### Global vs Local settings

We should have global settings that we can override locally:
in global settings add a button to force setting to all (erasing local settings)
in local settings, add a checkbox to override global settings. Have a local and a global tab in the visualization panel.

This would be helpful for the color of sensors as well, which was actually a requested feature.

We can store the LineRadius in objects as a custom property I guess.

### SAPIENT Detections as Entities

Should SAPIENT detections be entities as well? Probably not, would overflow our UI. Still, would be nice to have a local setting, such as line radius for objects.