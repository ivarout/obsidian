#work
## To Do

- [ ] target parameters local and global, find a good way to keep stuff synced, with as little callbacks as possible
	- [ ] When syncing entities (on EntityAdded/EntityRemoved event), call view.update_target_parameters in the sync entities function, then also update global target parameters, using a function maybe \_update_global_target_parameters. 
	- [ ] On update AOE Range model should maybe be a separate event, cuz we don't have to sync entities here.
- [ ] sync_entities add/removes coverage visualization, and updates local target_parameters (and global maybe as well, they are ignored anyways when target is ignore)
- [x] flashing material should have same base color in detector etc.
- [ ] Properly updates views when target properties/parameters change.
	- [x] When selecting database, immediately update target_types as well
- [ ] Fix geometry nodes 
	- [ ] No need to replace entire node groups, just use mod.node_group.interface_update or something like that.
- [ ] Update 'target_global' implementation
- [ ] check updates when changing target parameters in view, or in entity
- [x] immediately apply range after adding entity.
## Wrap-Up


## Brain Dump

