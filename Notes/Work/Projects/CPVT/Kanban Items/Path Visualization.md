[[CPVT Kanban]]

Use Geometry Nodes for Ground projection along entire path, both sapient paths, and user defined paths.

As a vertex attribute, we store birthframe, so we know when to show a specific vertex.

- [x] Use geometry nodes for path visualization
- [x] (cancelled) store previous position as attribute, so we don't calculate ground projection every frame for every vertex, only those not yet calculated, In that case, it is probably fine to just depend on raycast, only whenever we don't have a previous position yet. This probably won't work so well, we can't permanently store stuff in the geometry nodes modifier, just use refresh instead.
- [ ] Fix setting line radius, simply updating default value doesn't apply to existing path objects. rather use the same approach as used for the CPVT Object Scale.
- [ ] store birth frame so we know when to show stuff.
- [ ] have refresh function, in case terrain is updated we need to update the ground projections too.
- [ ] store distance since start as vertex attribute, so we can show distance travelled and distance to end.
- [ ] (optional) Use to common click map operator
- [ ] Would be nice to allow for global settings with an optional local override

## Geometry Nodes
- [ ] extruded point at the end can look janky sometimes...
- [ ] Propertly update all geometry node modifiers, e.g. when updating global line radius. We want to keep local overrides though maybe...
- [ ] 
