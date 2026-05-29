---

kanban-plugin: board

---

## To Do

- [ ] Add obstruction to rf calculations
- [ ] LUT for RCS using the asset_manager
- [ ] GNSS considerations
	
	- use carrier to noise density C/N0 (basically SNR) 
	- Be aware that this may not always be fair. Especially for BOC modulation type (check gemini), in the case of multipath, or a narrow filter.
- [ ] use bitmask in ecs, also store map for type to its derived types, so we easily get all bitmasks when we need to access multiple derived types, e.g. all RFReceivers.
- [ ] Documentation
	
	- [ ] component decorator
	- [ ] update yaml doc a bit, now that check_yaml_hook is to be called manually.
	- [ ] avoid forward references in component annotations, especially when relying on them for serialization, get_type_hints will flip.
- [ ] support infinity bound in collisionbox (e.g. for ground)
- [ ] Maybe just always have the animation running in Blender. This will update the UI, even when the simulation is paused. Basically calling ecs.update() with delta_t 0 when paused.  UI elements can still use system delta t if necessary


## In progress

- [ ] Add RotationTweenPhysical (using max rotation/angular acceleration): When looking at TweenPhysical, the direction will be the axis of rotation, and the distance will be the total angle
- [ ] Document everything
- [ ] Move RF/GNSS stuff to cpst-modules, not in the core repository
	
	we'll have the following repositories:
	
	cpst-core
	cpst-modules
	cpst-gui
	
	whatever other people want to build on top of this of course.
- [ ] Add update rate as property in systems (e.g. once every 10 frames, or maybe specify in seconds)
- [ ] **Create example**
	
	Have drone move to target if it has RF Signal, if jammed, it will wait 10 seconds, then land
	
	Have an RF detector and Jammer, and demonstrate handoff.
- [ ] Add max angular velocity and acceleration to kinematic body
- [ ] Add max torque and intertia to RigidBody


## Done

- [ ] Add rotationTween
- [ ] <details>
	<summary> Finish behavior Tree </summary>
	
	- [x] Add to yaml implementation
	- [x] Have working nodes and sequences and selectors working and tested
	- [x] Have some action nodes that are spawned by tree nodes
	
	</details>
- [ ] Implement Wind component (constant only for now)
- [ ] Implementation Simple Navigation And Guidance (PN will come later)
- [ ] define to_yaml from_yaml for antenna gain model
- [ ] disabled \_check_yaml for now, having default arguments for everything often doesn't make sense i think.
- [ ] Have some RF overlap logic for GNSS and RF communictaion
- [ ] **20260327**
	
	Implement UpdateRFCommsLinks and UpdateRFDetectors similar to barrage jammers. Then create some tests to check if everything works as expected.
- [ ] Test barrage jammer received noise
- [ ] fix overloads, e.g. get_entities_with_components. right now, ide thinks we're returning types/classes, rather than instnaces.
- [ ] **20260330**
	
	Test system sorting
- [ ] <details>
	<summary>Add Comms</summary>
	
	- [x] have groups that can communicate together?
	- [ ] Add and remove commslink based on events.
	</details
- [ ] Events like ComponenRemovedEvent, EntityRemoveEvent, ComponentChangedEvent, etc.
- [ ] **Feed-forward vs Feed-back**
	
	distinguish between predictable and non-predictable forces somehow (so we now if they should feed directly into the steering command through feed forward, or use a feedback loop instead).
	
	Nah, just turn on or off gravity, way easier.
- [ ] 




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false]}
```
%%