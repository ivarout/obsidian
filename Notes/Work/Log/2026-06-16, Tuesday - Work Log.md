#work
## To Do

- [ ] 
## Wrap-Up


## Brain Dump

### License bullshit

newer yolo version have gnu (viral) license, which forces you to make your software open source, and can't put restrictions on redistribution. even trained models inherit AGPL-3.0 license. So if we train on sensitive data, and share that with someone, we can't put restrictions on resharing. You can buy a license from ultralytics if you want though.

If we use the trackers only internally, no worries. Also, if we share the dll without any onxx models, no big deal right, it's just yolo, which is publicly available. Though maybe the hybrid approach for SOT is something we might not wanna share.

bytetrack and botsort use MIT (permissive license), so no problem here. We could use darknet yolo with bytetrack and botsort, which allows us to use any license we want. Let's try this route first.

SAM2 uses apache 2.0, which is a permissive license, just state that you used SAM2, and state whether/where you made changes to the original SAM2 code, probably nowhere though, just using the library.



