#work
## To Do

- [ ] Defer raised events using a timer. This a
## Wrap-Up


## Brain Dump

### Application Timers in Update Callback

Think about doing stuff using timers, defer things like adding objects, changing materials etc. This is probably safer. Note that timers are automatically removed is they return None. Use first_interval to set the amount of time to wait before the first run.
