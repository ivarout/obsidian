#work
## To Do

- [x] Add option to defer when emitting event, which is safer for complex operations. Also think about avoiding running an event many time, e.g. when moving a slider.
	- [x] play around with coalesce and defer, does everything work as expected?
- [x] Use new Events for team updates, and system updates. Replace all subscriptions
- [ ] Have local scale that can be used as override. Local vs Global visualization, determine how to implement
- [ ] Use inheritance more, e.g. effector and detector are mostly the same no? This would avoid some duplicate code.
- [x] Why does Coverage.update_target_parameters go over all views? because target can be global!
- [x] in Coverage, remove_entity (and add_entity and some other functions), determine if it makes more sense to pass the context or the scene.
## Wrap-Up

Tomorrow, look at and fix the Coverage. remove_entity function, which gets scene instead of context. Which makes more sense though....

Need to work on local visualization overrides (also for coverages)

Eventually, replace all custom properties with new and easier event system.

## Brain Dump

### Application Timers in Update Callback

Think about doing stuff using timers, defer things like adding objects, changing materials etc. This is probably safer. Note that timers are automatically removed is they return None. Use first_interval to set the amount of time to wait before the first run.
