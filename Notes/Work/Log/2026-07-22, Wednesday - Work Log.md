#work
## To Do
 - [x] Add local scale override option (use get_transform)
 - [x] Add local color override option (use get_transform)
 - [x] Add "use selection handlers" option to the addon settings
 - [x] Add dev options again.
 - [ ] See if we can simplify coverage view implementations (using the new event-subscription system)
	 - [ ] move more stuff to base class
	 - [ ] use get/set_transform for view_group_id
	 - [ ] use get/set_transform for name_ui
 - [ ] use color override in coverage views
 - [ ] use get_transform for entity.disabled and entity.active so we don't need the is_disabled and is_active properties anymore.
 - [ ] we can use the new get_transform, set_transform for much cleaner implementations of global/local target and everything that follows either global or local settings.
 - [ ] use 'set_string_transform' for setting paths. 
- [ ] fix bug with sapient when jumping to frame 
- [ ] Fix bug with line radius to ka not applying immediately
- [ ] Work on path visualization user defined paths
- [ ] fix path remaining distance in ui
- [ ] new scene time implementation

## Wrap-Up


## Brain Dump

Use 'area.tag_redraw' on properties window if it doesn't properly update.