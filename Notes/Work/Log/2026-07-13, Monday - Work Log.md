#work
## To Do

- [x] Add option to defer when emitting event, which is safer for complex operations. Also think about avoiding running an event many time, e.g. when moving a slider.
	- [x] play around with coalesce and defer, does everything work as expected?
- [ ] Use new Events for team updates, and system updates. Replace all subscriptions.
- [ ] Have local scale that can be used as override
- [ ] Local vs Global visualization, determine how to implement
- [ ] Use inheritance more, e.g. effector and detector are mostly the same no?
## Wrap-Up


## Brain Dump

### Application Timers in Update Callback

Think about doing stuff using timers, defer things like adding objects, changing materials etc. This is probably safer. Note that timers are automatically removed is they return None. Use first_interval to set the amount of time to wait before the first run.
