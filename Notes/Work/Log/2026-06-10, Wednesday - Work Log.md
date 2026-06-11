#work
## To Do

- [ ] Check all information available
	- [ ] promising trackers document by Mees Beumer
	- [ ] trackers mentioned in email by Bart and Mees: **trackerCSRT** (**Channel and Spatial Reliability Tracking**), **SAM Tracker**, **YOLO**/Darknet
- [x] Run TrackerCSRT and TrackerKCF in Python, just to get a feel of how it's used
- [ ] Check C++ interface code written by Krister
- [ ] Check promising trackers to implement in C++ dll, there seems to be interest in yolo/darknet
- [ ] Get a bit familiar with YOLO in python
	- [ ] check how to change settings such as botsort and using re-id
- [ ] Check how to implement yolo in C++
- [x] Meeting with Chris Rainer on Regions and LineToTarget.
## Wrap-Up

First, we need to figure out how to configure yolo and botsort (or bytetrack), e.g. to keep track ids more confidently, check how to enable re-id etc. even though this will make things potentially too slow, it gives us a baseline

Then, we need to check how we can implement this completely in C++ with zero python dependencies.

Couldn't join meeting with chris due to microsoft teams restrictions, we emailed instead. He asked for suggestions on Blender version, Line to target visualization, and Chris will keep working on regions, and we'll call next week.
## Brain Dump

#### YOLO and Botsort
There seems to be interest in using YOLO, but this **spawns its own tracks**, whereas the current suggested tracker dll interface only allows for the user to manually spawn new tracks. One track per instance seems limiting. Why not create one instance of the tracker that can spawn/hold multiple tracks. Then we can query all tracks with a single function, or a specific track by providing an id.

Start with using YOLO and **bytetrack** or **botsort** (the default). botsort is more accurate but slower. since it is the default for yolo v11, start with this.

To stick to Kristers API, we want to draw a region of interest, then track the object we marked. Do use this in combination with yolo, check the yolo detection that has the biggest IoU with our specified region of interest.

We have to determine the best approach to create some tolerance for lost tracks, increase frame_buffer in botsort (or yolo?) options, if new track id is assigned, check if this is not the same track anyways, by comparing IoU with previous frame(s) and cls.

Yolo26 better for lightweight hardware