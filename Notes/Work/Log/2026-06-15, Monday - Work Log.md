#work
## To Do

- [ ] Do this later... ~~Add some backup against track-id changes, if bounding box is similar enough, update track id, test this with weaker tracking like bytetrack, we should include color histogram1~~
- [ ] Check interface by Krister
- [ ] Check python-less implementation of yolo
## Wrap-Up


## Brain Dump

- we should probably ignore the class when trying to re-acquire a track, yolo might switch class, e.g. between a bird or a plane. We just want to follow whatever we picked initially, whether it's a bird or a plane.
- We have to add re-aquisition logic, if a track is lost, compare new tracks:
	- compare bbox distance
	- compare bbox dimensions
	- compare (only if previous two passed) a color histogram with original detection. The color histogram is to be gradually updated (blend of previous with current) instead of completely overwriting it, to prevent sudden changes in e.g. lighting to have a huge effect.
- Shortcoming of yolo is that it can only track what it knows. If we want to track a specific type of airplane, we had better have a model trained on that type of airplane.
- First, lets just try to get yolo running in a DLL, then think about a hybrid approach, where we add re-acquisition logic.