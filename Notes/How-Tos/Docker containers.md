## Nextcloud

### Video thumbnails

Open a console in the docker container, e.g. using portainer, and install ffmpeg:

```

apt-get update
apt install ffmpeg
```

In the `config.php` file, ensure you have previews enabled for videos, which should look something like:

```php
 'enable_previews' => true,  
 'enabledPreviewProviders' =>    
 array (  
   0 => 'OC\\Preview\\Image',  
   1 => 'OC\\Preview\\Movie',  
   2 => 'OC\\Preview\\TXT',  
   3 => 'OC\\Preview\\MP3',  
   4 => 'OC\\Preview\\MKV',  
   5 => 'OC\\Preview\\MP4',  
   6 => 'OC\\Preview\\AVI',  
   7 => 'OC\\Preview\\MOV',  
   8 => 'OC\\Preview\\MP3',  
   9 => 'OC\\Preview\\PNG',  
   10 => 'OC\\Preview\\TXT',  
   11 => 'OC\\Preview\\MarkDown',  
 ),
```

### Generate Previews for everything 

1. Install the 'Preview Generator' addon in the nextcloud UI.
2. In the console in the nextcloud docker container, run `apt-get update && apt-get install ffmpeg imagemagick ghostscript`
3. in the console in the nextcloud docker container, run `php occ preview:pre-generate -vvv`
