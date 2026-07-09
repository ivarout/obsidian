[[CPVT Kanban]]

Use Geometry Nodes for Ground projection along entire path, both sapient paths, and user defined paths.

As a vertex attribute, we store birthframe, so we know when to show a specific vertex.

- [ ] Use geometry nodes for path visualization
- [ ] store previous position as attribute, so we don't calculate ground projection every frame for every vertex, only those not yet calculated, In that case, it is probably fine to just depend on raycast, only whenever we don't have a previous position yet.
- [ ] store birth frame so we know when to show stuff.
- [ ] have refresh function, in case terrain is updated we need to update the ground projections too.
- [ ] store distance since start as vertex attribute, so we can show distance travelled and distance to end
- [ ] (optional) Use to common click map operator