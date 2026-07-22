#work
## To Do
 - [x] Add local scale override option (use get_transform)
 - [x] Add local color override option (use get_transform)
 - [x] Add "use selection handlers" option to the addon settings
 - [x] Add dev options again.
 - [x] removed 'collection' entity, there's no point really. Just support use platform entity (and implement custom relationship lines with geometry nbodes)
 - [x] big overhaul to 'entity' class, replacing many update function with emitting event, which is much more flexible, and probably safer
 - [x] Removed entity.is_active and entity_is_disabled, use the net get_transform function for rna properties, which is much easier to implement.
 - [ ] See if we can simplify coverage view implementations (using the new event-subscription system)
	 - [ ] move more stuff to base class
	 - [ ] use get/set_transform for view_group_id
	 - [ ] use get/set_transform for name_ui
 - [ ] use color override in coverage views
 - [x] use get_transform for entity.disabled and entity.active so we don't need the is_disabled and is_active properties anymore.
 - [ ] we can use the new get_transform, set_transform for much cleaner implementations of global/local target and everything that follows either global or local settings.
 - [ ] use 'set_string_transform' for setting paths. 
- [ ] fix bug with sapient when jumping to frame 
- [ ] Fix bug with line radius to ka not applying immediately
- [ ] Work on path visualization user defined paths
- [ ] fix path remaining distance in ui
- [ ] new scene time implementation

## Wrap-Up

Continue with cleaning up the coverage views and supporting the entity color override option.
## Brain Dump

Use 'area.tag_redraw' on properties window if it doesn't properly update.