<h1>NGINX-based Media Streaming Server / RTMP / FFMPEG SERVER</h1></br>
(https://hub.docker.com/r/murderousone/nginx-ffmpeg-rtmp)
</br>
</hr>
<p>THIS DOCKER IMAGE WILL WORK WITH 64 Bit Systems.</br>
<h2>LIGHTWEIGHT - IMAGE WILL CONTAIN REALLY SIMPLE SHELL SCRIPTS TO MAKE LIFE EASIER. NOTHING CODE SAVY</h2></br>
<b>DOCKER IMAGE MAY NOT WORK WITH  32bit Systems.</b></br>
<p>Image can be attached too and container is fully customizable.</p>
<p>Image has simple pre-installed bash scripts to make running the server easier.</p>
<h2><p>Based on Ubuntu Server Latest LTS 64 Bit </p></h2>
<h2><p>Based on Ubuntu Server Latest LTS ARM64 for Raspberry Pi4 / Pi400 </p></h2>
<hr>
</br>
<h1>UPDATES FOR UBUNTU SERVER LATEST LTS</h3>
* COMPILED WITH NGINX RTMP MODULE - NGINX v1.28.0</br>
* COMPILED WITH FFMPEG Version 7.1.1 - use image tag: ubuntu-latest</br>
* EASY INIT SCRIPT FOR NGINX START, RESTART, STOP</br>
* EASY SHELL EXECUTABLE SCRIPTS FOR EDITING, NGINX START, RESTART, STOP AND EASIER MANAGING YOUR RTMP SERVER</br>
* ALL UBUNTU PACKAGES UPDATED</br>
</hr>
<h1>UPDATES FOR RASPBERRY Pi4 / Pi400</h3>
* UBUNTU SERVER LATEST LTS ARM64</br>
* COMPILED WITH NGINX RTMP MODULE - NGINX v1.28.0</br>
* COMPILED WITH FFMPEG 7.1.1 - use image tag: ubuntu-arm64</br>
* EASY INIT SCRIPT FOR NGINX START, RESTART, STOP</br>
* EASY SHELL EXECUTABLE SCRIPTS FOR EDITING, NGINX START, RESTART, STOP AND EASIER MANAGING YOUR RTMP SERVER</br>
* ALL UBUNTU ARM64 PACKAGES UPDATED</br>
</hr>
<h1>NGINX-based Media Streaming Server Features</h1>
<p>
	* RTMP Video on demand FLV/MP4, playing from local filesystem or HTTP<br>
	* Stream relay support for distributed streaming: push &amp; pull models<br>
	* Recording streams in multiple FLVs<br>
	* H264/AAC support<br>
	* Online transcoding with FFmpeg<br>
	* HTTP callbacks (publish/play/record/update etc)<br>
	* Running external programs on certain events (exec)<br>
	* HTTP control module for recording audio/video and dropping clients<br>
	* Advanced buffering techniques to keep memory allocations at a minimum level for faster streaming and low memory footprint<br>
	* Proved to work with Wirecast, FMS, Wowza, JWPlayer, FlowPlayer, StrobeMediaPlayback, ffmpeg, avconv, rtmpdump, flvstreamer and many more<br>
	* Statistics in XML/XSL in machine- &amp; human- readable form
</p>
</hr>
<p>
	<span style="color:#3498db;"><strong>ENJOY!&nbsp;</strong></span>
</p>

<h1>NGINX-based Media Streaming Server / RTMP / FFMPEG SERVER</h1>

<p>Docker image is a ubuntu x64 or Debian latest nginx/ffmpeg base os which contains all the configuration created for setting up a streaming server</p>
<p>The docker image is also unlocked and contains pre-made bash scripts to run your streaming server even easier than our manual setup.</p>
<p>Docker also allows better performance and less resources to your computer / server.</p>

<h2> Install Docker on Linux</h2>

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

<a href="https://docs.docker.com/get-docker/" target="_blank">INSTALL DOCKER FOR OTHER NON-LINUX OS's</a>

<h2>RUN THE DOCKER CONTAINER WITH DOCKER COMPOSE</h2>

<h3>Install Docker Compose on Linux</h3>

```
sudo curl -L "https://github.com/docker/compose/releases/download/v2.36.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
<p><a href="https://docs.docker.com/compose/install/" target="_blank">To install Docker Compose on other non-Linux OS's </a></p>

<h1>Downloading and Creating your container Using docker-compose (Ubuntu Image)</h1>

<h3>Create a new Directory</h3>

```
mkdir nginx-rtmp
```

<h2>Create a Docker Compose file inside your new directory:</h2>
<p>(example: docker-compose.yml)</p>

<h2>Change Directory</h2>

```
cd nginx-rtmp
```

<h3>Create the docker compose file:</h3>

```
nano docker-compose.yml
```

<p>COPY and PASTE the code below for Ubuntu OS Container and Save</p>

```
services:
  nginx-rtmp-streaming-server:
    image: murderousone/nginx-ffmpeg-rtmp:ubuntu-latest
    volumes:
      - nginxconfig:/usr/local/nginx/conf/
    container_name: m1gc-nginx-rtmp-server
    restart: unless-stopped
    stdin_open: true
    tty: true
    ports:
      - "80:80"
      - "443:443"
      - "1935:1935"

volumes:
  nginxconfig:
```


<hr>
<h2>Downloading and Creating your container Using docker-compose (Raspberry Pi4 Ubuntu Arm64 image)</h2>

<h2>Create a new Directory</h2>

```
mkdir nginx-rtmp
```

<h2>Change Directory</h2>

```
cd nginx-rtmp
```

<h2>Create the docker compose file:</h2>

```
nano docker-compose.yml
```

<h2>COPY and PASTE the code below for Raspberry Pi Ubuntu OS Container and Save</h2>

```
services:
  nginx-rtmp-streaming-server:
    image: murderousone/nginx-ffmpeg-rtmp:ubuntu-arm64
    volumes:
      - nginxconfig:/usr/local/nginx/conf/
    container_name: m1gc-nginx-rtmp-server
    restart: unless-stopped
    stdin_open: true
    tty: true
    ports:
      - "80:80"
      - "443:443"
      - "1935:1935"

volumes:
  nginxconfig:
```
<hr>

<h2>To update the container with Docker Compose:</h2>
<p># Pull the latest image / update</p>

```
docker-compose pull
```

<p># To Create, Start, Update and Restart the container</p>

```
docker-compose up -d
```
<a href="https://asciinema.org/a/422102" target="_blank"><img src="https://asciinema.org/a/422102.svg" /></a>

<p>Stop containers and removes containers, networks, and images created by up</p>

```
docker-compose down 
```
<p>Above docker command will pull the image, create, run and start the Docker Container / Streaming Server already configured with ports opened. </p>
<p>IF YOU UPDATE THE DOCKER IMAGE TO A NEW VERSION, DOCKER COMPOSE WILL RECREATE THE DOCKER CONTAINER WITH THE NEW IMAGE UPDATES. </p>
<p>WHEN DOCKER COMPOSE RECREATES THE DOCKER CONTAINER, ANY CONFIGS CHANGES MADE TO THE CONTAINER WILL NOT BE DELETED </p>
<p>VOLUMES WILL BACKUP YOUR CONTAINER NGINX CHANGES AND WILL REQUIRE A VOLUME DELETE TO GO BACK TO DEFAULTS BUT IS OPTIONAL</p>
<hr>

<h2> List and Delete Volumes </h2>

<h3> List Docker Volumes </h3>

```
docker volume ls
```

<h3> Delete Docker Volumes </h3>

```
docker volume rm volume_name volume_name
```

<h2>YOU CAN EXECUTE THE SCRIPTS FROM OUTSIDE THE CONTAINER WITHOUT ATTACHING USING DOCKER EXEC</h2>

```
docker exec  nginx-rtmp-server ./restart-rtmp
```

<h2>OR Attach to the Running RTMP Docker Container</h2>
<p>NOTE: I LIKE TO KEEP THE IMAGE COMPLETELY TRANSPARENT / INSPECTABLE / ATTACHABLE / SIMPLE /
U CAN ACCESS THE ENTIRE FILE SYSTEM IMAGE, EDIT, UPDATE, INSPECT THE FULL OS / MAKE ANY CHANGES OF YOUR OWN.
</p>

```
docker attach nginx-rtmp-server
```

<h2>To Update the server packages on the NGINX / RTMP Docker Container
</h2>

```
./upgrade
```

<h2>Edit and Add your Stream Key and URL's & Set your RTMP Servers Stream Key to the RTMP Config</h2>
<p>Stream URL / Key from Restream.io, Youtube, Twitch</p>
<p>(Example: - Change -> push rtmp://live.restream.io/streamkey;)</p>
<p>SETTING RTMP SERVERS STREAM KEY  (Can be named anything, No spaces.)</h2>
<p>(EXAMPLE: Change -> rtmp://127.0.0.1/live/YOURSTREAMKEY to rtmp://127.0.0.1/live/ANY-KEYNAME-YOU-WANT)</p>
<img src"https://m1-gamingz.com/wp-content/uploads/2021/03/Screenshot-2021-03-27-130647-live.png"></img>

```
./edit-rtmp
```
<h5> NOTE: Must be attached to container to edit.</h5>

<p>If you wish to use FFMPEG</p></br>
<b>FFMPEG LOCATION: </br></br>
<b>/usr/bin/ffmpeg</b> </br>
<b>/usr/share/ffmpeg</b> 

<h2>START THE RTMP SERVER</h2>

```
./start-rtmp
```

<h2>STOP THE RTMP SERVER</h2>

```
./stop-rtmp
```

<h2>RESTART THE RTMP SERVER</h2>

```
./restart-rtmp
```

<h2>EXIT THE CONTAINER WHILE LEAVING IT RUNNING</h2>

```
HOLD: CRTL + p + q 
```

<hr>

<h2>VIDEO ON HOW TO INSTALL, EDIT AND RESTART USING BASH SCRIPTS</h2>

[![asciicast](https://asciinema.org/a/TQqFawEeYd1vs0oycUtXI3NRS.svg)](https://asciinema.org/a/TQqFawEeYd1vs0oycUtXI3NRS)

<p>Check the Video Above to View How To Setup. Edit, and Restart Using The Bash Scripts Provided....</p>

<p>Your docker streaming server is now started and running in the background...</p>
<p>You can now connect to it, using your preferred streaming software. (obs studio, xsplit, vmix, streamlabs obs, etc)</p>

<h1>Setting up main computer to stream to NGINX / RTMP / FFMPEG</h1>
<p>Any ol PC with OBS Studio & NVENC encoding.</p>
<p>In OBS, i use NVENC encoding and I use my monitor’s native resolution (1080p).</p> 
<p>Using OBS Studio, in your broadcast settings you need to use the “Custom” streaming service.</p>
<a href=""><img src="https://i.imgur.com/mLJoJbJ.png" alt="M1GC">
</a>

<p>The Streaming URL will be something like rtmp://192.168.1.100/live (Use your own server’s IP).</p>
<p>Your Stream Key needs to be the same you used in your nginx configuration. </p>
<p>(Example: KEYNAME-YOU-SET)</p>

<p>In the Encoding, use <a href="https://www.nvidia.com/en-us/geforce/guides/broadcasting-guide/" target="_blank">NVIDIA NVENC</a> (Since it doesn’t use a lot of CPU).</p>

<h3>Bit-rates</h3>

<p>Click <a href="https://support.google.com/youtube/answer/2853702?hl=en" target="_blank"> here</a> for Live encoder best settings for bit-rates, and resolutions</p>
<p>You may need to reduce your bit-rate depending on services bandwidth limits.</p>
<p>You may need to adjust your max bit rate according to your needs and capabilities</p>

<h3>AUDIO</h3>

<p>As for Audio encoding, I use the AAC codec, 160 bit rate and a Format of 44 or 48 Khz.</p>

ENJOY!
