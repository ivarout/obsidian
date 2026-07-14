#work
## To Do

- [ ] more event subscription deferred logic to the subscribe_to_event function. This makes more sense because we want to control whether a subscription should be deferred on a per-subscription basis. How to check if we already subscribed something though...
- [x] Replace more subscriptions with new event system
- [ ] Local vs global visualization settings, such as scale, color, etc.
- [ ] Think about using inheritance more, e.g. for effectors and detectors, which are very similar...
- [ ] Path visualization.
- [ ] Replace deprecated event system with new one.
## Wrap-Up

First thing to do is check and maybe fix the emit_event function (check if defer and run_once work, set first_interval_time to 1, and test out with the global scale for example).
## Brain Dump

Would we be better off without the ***PropertyCollection***, and instead make different entity classes for each type? e.g. RadarEntity, etc. This would give us more control over the parameters at least. Would actually be an easier implementation.

instead of subscribable, provide an EventContext when creating a PropertyCollection. Whenever a property updates, it will emit the specified event.