#todo 

- [ ] Setup UFW, also block internal traffic. Only allow wireguard and specific ip addresses. Internal smart devices cannot be trusted.
	- [ ] Should we allow ssh? Not really, we can ssh through wireguard, that should be enough.
- [ ] Setup nginx to allow only wireguard traffic to be redirected to entire internal network, or only some very specific ip addresses, like nextcloud/s/  [[../Notes/To-Dos/Set up nginx with wireguard]]