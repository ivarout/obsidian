#work
## To Do

- [ ] Add option to defer when emitting event, which is safer for complex operations. Also think about avoiding running an event many time, e.g. when moving a slider.
	- [ ] play around with coalesce and defer, does everything work as expected?
## Wrap-Up


## Brain Dump

### Application Timers in Update Callback

Think about doing stuff using timers, defer things like adding objects, changing materials etc. This is probably safer. Note that timers are automatically removed is they return None. Use first_interval to set the amount of time to wait before the first run.
