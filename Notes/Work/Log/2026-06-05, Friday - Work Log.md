#work #CPVT
## To Do

- [x] Use height wrt ground in geometry nodes (instead of using raycast within geometry node)
	- [x] Check why the object position is a little bit ahead of the curve visualization, i dunno, looks okay i guess...
- [x] Create path geometry nodes modifier in python
	- [x] Don't store direct reference to bpy.types.GeometryNodeGroup, this reference will be invalidated pretty quickly. Access by name instead.
- [ ] We need a refresh function that recalculates heigh wrt ground in EdgeNodeEntity detection archive, in case we update the terrain, probably bind this to f5, since it's terrain related.
- [ ] make stuff stand out with highly emmissive materials.
## Brain Dump

## Wrap-Up

The path visualization for imported sapient logs seems to work well. We should make the emmissivity work by default, at least for the distribution package. Next up, we should look at applying the new Path visualization using geometry nodes to user defined paths as well.