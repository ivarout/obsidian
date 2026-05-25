#todo

- wireguard lives behind nginx, giving extra protection to stuff like my nextcloud data, which can now never be accessed by anyone without the wireguard certificate
- To still be able to have people access my public shared file links, use a url filter, that will allow requests containing /s/ (nextcloud's format for shared links), but block everythin else, e.g.:

```nginx
server {
    listen 443 ssl;
    server_name yourcloud.com;

    # 1. ALLOW public share links
    location /s/ {
        proxy_pass http://nextcloud_container:80;
        # Standard proxy headers here...
    }

    # 2. ALLOW necessary static assets for the share page to look right
    location ~* ^/(common|core|apps|dist|themes|settings)/ {
        proxy_pass http://nextcloud_container:80;
    }

    # 3. BLOCK everything else (Login page, Dashboard, etc.)
    location / {
        return 403; # Or redirect to a 404/Home page
    }
}
```


some other snippet, which shows how nginx allows the above stuff (minus the assets, probably have to add this too), and allows only those on the wireguard vpn to access nextcloud

```nginx
server {
    listen 443 ssl;
    server_name cloud.yourdomain.com;

    # PUBLIC: Anyone can see share links
    location /s/ {
        proxy_pass http://nextcloud:80;
    }

    # PRIVATE: Only accessible if your WireGuard VPN is ON
    location / {
        # Replace with your actual WireGuard internal subnet
        allow 10.8.0.0/24; 
        
        # Block everyone else
        deny all;          

        proxy_pass http://nextcloud:80;
    }
}
```