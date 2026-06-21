#work

## To Do

- [x] Have running example of SAM2
	- [x] Can we create a C++ dll for this? Yes, but will be a bit of work.
	- [x] Do we really have to write temp frames to disk? yeah probably, too much to load into ram.
	- [x] Will smaller models without cpu offloading work well still? yes, not a real speed improvement though.
	- [x] Can we reach 20/30 fps somethow? Run in compiled mode? i'm not so sure, we seem both ram and vram constrained on our nlr laptop.
	- [x] Can we get autocomplete to work? Add folders to python.analysis.extraPaths~~
- [ ] Have running example of Yolov3 + tracker (permissive license)
- [ ] probably tomorrow, get started on C++ implementation, at least have enough for meeting.
## Wrap-Up


## Brain Dump

Een eigen baseline voor tracking gebruiken, welke baseline?

onxx runtime is a lightweight inference engine, which is good for small edge devices. We hence need to export our model 
### SAM2

- pro: track single object without any training
- pro: good with occlusion
- pro: very permissive license
- con: SAM may switch objects on crowded scenes with many objects.
- con: Probably works ok on pre-recorded video (by batching frames), less so on live frame-by-frame streams (to be investigated though).

it returns a binary mask, i.e. which pixel belongs to the detection (we could convert this to a bounding box of course, though we lose some information). This is another good addition to the interface maybe, allow for a detection mask to be queried.

It's very slow, we get about 2 fps with the large model (vram constrained i think), and maybe 4 ish with the small model, which isn't very strong. Maybe we're supposed to get higher fps, like 20 fps, but haven't managed to do so yet.
### YOLO

- We have to change some thresholds in the botsort.yaml or bytetrack.yaml tracker config, so as not to throw away tracks too easily, since currently rely on the track id staying the same. If it changes, we lose our track. We can add robustness to this in the future, by comparing new detections bounding_box location and dimensions, as well as color histogram, to last known detection (the histogram filter should slowly update, e.g. mix 90% with 10% of new historgram)

- implement yolov4 from https://github.com/AlexeyAB/darknet 
### Hybrid approaches

it might be a good idea to combine very strong with very fast algorithms, e.g. run 

### OpenCV vs CUDA

Are we okay with a CUDA dependency, will work on e.g. jetson

**ONNX Runtime** C++ API vs **NVIDIA TensorRT** C++. Lightweight footprint, broad hardware support (CUDA, DirectML, OpenVINO), vs Real-time production pipelines, lower latency, highly optimized VRAM utilization.

**Using OpenCV's DNN Module:** If you just need inference without TensorRT, OpenCV can read `.cfg` and `.weights` directly in C++ via `cv::dnn::readNetFromDarknet()`, then save it back out.