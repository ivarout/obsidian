#work
## To Do

- [x] Replace old event system with new one
- [ ] Add logging to new event system
- [ ] Make distinction between ui and simulation (check gemini for better name) events
- [x] Need to have more control over event scene updates. Effectors need to respond to Detectors for example. Initialize, pre-update, update, and post-update may be enough?
## Wrap-Up

Replaced effector entity interactions with new event system.
## Brain Dump

Maybe we need to add more event stages in CPVT, so we can control the order a bit better, like effectors responding to detectors.