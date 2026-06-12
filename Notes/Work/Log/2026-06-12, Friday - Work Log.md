#work
## To Do

- [ ] Check if a solid implementation of YOLO tracker with initial roi is feasible in python
- [ ] Check how to change yolo config, e.g. use re-id for botsort
- [ ] Check YOLO darknet vs normal YOLO
- [ ] Check SAM and TAM
- [ ] Check C++ interface written by Krister
- [ ] Check how stuff can be implemented in C++
## Wrap-Up

Played with yolo and tracking algorithms botsort and bytetrack in python. We draw an initial region, and if there is an IoU with a yolo detection that's high enough, start track. We need to lower the thresholds a bit to make sure that we don't throw away tracks too easily. Add another bit of logic to swap track-ids, since botsort/bytetrack sometimes change the track id in case of sudden changes.
## Brain Dump

We can of course draw an ROI, then check which YOLO detection in frame 1 has the highest IoU (with some minimum), and track that. This would work in the current tracking API by Krister. If not constrained by the API, some better option may be to let YOLO detect 1 frame, then let the user select which detection to track.

Where does **user input** come in? is it okay to have the dll prompt for user input? e.g. ask the user to select a detection object to track? Probably not I guess right. But how does this work for the other trackers then? We want a shared front-end too? e.g. some popup window allowing the user to specify the roi

instead of a bounding box, might be nice to also add a mask as input for tracking algorithm, i.e. which pixels are interesting. On the front-end, we could use a segmentation algorithm to create such a mask for us (maybe SAM or TAM are good for this?)

How much do we want to keep the current tracker API? We could always add new interface functions i guess. For dlls that don't support e.g. a mask, the mask could be converted to an ROI by simple taking the min-max pixel values of the mask.

Yolo with botsort seems to work okay. The tracked pidgeon even recovers from obstruction by a human. We needed to lower some thresholds in the botsort.yaml config, to avoid it from discarding tracks too quickly. And also increased the frame buffer a bit (i.e. keep previous tracks around for more frames after we lost em).

One instance per track id (as required by the API) is not great for yolo. For don't want to have separate yolo instances running for sure, this would be a huge waste, since yolo already tracks multiple objects, so we could very specify multiple ROIs and track all of them in a single instance. A solution that would fit within the API is to have the Tracker DLL use a singleton that contains the Yolo tracker instance, but this would prevent us from processing multiple cameras at the same time, at least when sharing  one OS process.

If we lose our track, but have a new track id at roughly the same position, assume it's the same (if IoU is high enough, and if it's the same cls).