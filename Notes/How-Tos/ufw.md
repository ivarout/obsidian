To allow all traffic for a specific app like syncthing:

```bash
sudo ufw allow syncthing
```

To allow incoming for a specific app like syncthing from a specific ip:

```bash
sudo ufw allow from 192.168.1.9 to any app syncthing
```

Note that if you want to assign a static ip to your phone, make sure it doesn't randomize its mac address for your home network.

To add a specific comment as well:

```bash
sudo ufw allow from 192.168.1.9 to any app syncthing comment 'allow syncthing incoming from phone'
```

To get the status and show rules:

```bash
sudo ufw status verbose
```

To get the rule numbers:

```bash
sudo ufw status numbered
```

To delete specific numbers:

```bash
sudo delete <rule number>
```
