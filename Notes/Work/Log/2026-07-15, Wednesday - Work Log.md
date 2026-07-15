#work
## To Do

- [ ] Fix event system, allow optional defer and run_once arguments in 'subscribe_to_event'. Actually add an update policy.
## Wrap-Up


## Brain Dump

What should we check when running events, should event context be a simple dataclass always, so we can compare them? and replace queued events if context is the same? probably not... Events like entity detected should be allowed to have duplicated. Just fix the run_once option, which is only relevant for stuff like global object scale, and other global options changing e.g. the scene visualization.

Multiple possible implementations for run once:
- only avoid duplicate events of same type if context is the same
	- This way we can have event of a specific entity detecting another specific entity set to run_once. Does it even make sense to have the exact same event type with the same context? Maybe sometimes...
- always avoid duplicate events of same type.
- Have an update policy
	- Run once per unique Event type
	- Run once per unique EventContext
	- Run every emit