
## Talk About

- talk about efficiency improvement for SAPIENT
	- object management / linger time
	- Efficient storage, huge array of detections combined with playback functionality can become very slow if not efficiently implemented (store in sorted dict, use bisect to very quickly find detections for specific point in time).
