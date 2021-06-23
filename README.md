<h1>NGINX-based Media Streaming Server / RTMP / FFMPEG SERVER</h1>
<a href="https://hub.docker.com/r/murderousone/nginx-ffmpeg-rtmp" target="_blank">DOCKERHUB IMAGE</a>
</hr>
<h1>NGINX-based Media Streaming Server / RTMP / FFMPEG SERVER</h1>
</hr>
</h2>IMAGE WILL CONTAIN SIMPLE BASH SCRIPTS TO MAKE LIFE EASIER</h2>
<p>THIS DOCKER IMAGE WILL WORK WITH 64 Bit Systems.</br>
<b>DOCKER IMAGE MAY NOT WORK WITH  32bit Systems.</b></br>
<p>Image can be attached too and is fully customizable.</p>
<p>Image has simple pre-installed bash scripts to make running the server easier.</p>
<h2><p>Based on Ubuntu Server Latest 64 Bit </p></h2>
<h2><p>Based on Debian Server Latest 64 Bit </p></h2>
</br>
<h3>UPDATES FOR UBUNTU SERVER LATEST</h3>
* Updated NGINX to the Latest Version - NGINX v1.20.1</br>
* COMPILED WITH NGINX RTMP MODULE</br>
* EASY INIT SCRIPT FOR NGINX START, RESTART, STOP</br>
* EASY SHELL EXACUTABLE SCRIPTS FOR EDITING, NGINX START, RESTART, STOP AND EASIER MANAGING YOUR RTMP SERVER</br>
* FFMPEG LATEST STABLE VERSION</br>
* ALL UBUNTU PACKAGES UPDATED</br>
</hr>
<h3>UPDATES FOR DEBIAN SERVER LATEST</h3>
* Updated NGINX to the Latest Version - NGINX v1.20.1</br>
*  COMPILED WITH ARUT's RTMP NGINX MODULE</br>
* EASY INIT SCRIPT FOR NGINX START, RESTART, STOP</br>
* EASY SHELL EXACUTABLE SCRIPTS FOR EDITING, NGINX START, RESTART, STOP AND EASIER MANAGING YOUR RTMP SERVER</br>
* FFMPEG LATEST STABLE VERSION</br>
* ALL DEBIAN PACKAGES UPDATED</br>
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
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
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
​
<h2>Change Directory</h2>

```
cd nginx-rtmp
```
​
<h3>Create the docker compose file:</h3>

```
nano docker-compose.yml
```

<p>COPY and PASTE the code below for Ubuntu OS Container and Save</p>

```
version: "3"
services:
  nginx-rtmp-streaming-server:
    image: murderousone/nginx-ffmpeg-rtmp:ubuntu-latest
    container_name: nginx-rtmp-server
    restart: unless-stopped
    stdin_open: true
    tty: true
    ports:
      - "80:80"
      - "443:443"
      - "1935:1935"
```

<h1>Downloading and Creating your container Using docker-compose (Debian image)</h1>

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

<p>COPY and PASTE the code below for Debian OS Container and Save</p>

```
version: "3"
services:
  nginx-rtmp-streaming-server:
    image: murderousone/nginx-ffmpeg-rtmp:debian-latest
    container_name: nginx-rtmp-server
    restart: unless-stopped
    stdin_open: true
    tty: true
    ports:
      - "80:80"
      - "443:443"
      - "1935:1935"
```

<h2>To update the container with Docker Compose:</h2>
<p># Pull the latest update</p>

```
docker-compose pull
```

<p># To Create, Start, Update and Restart the container</p>

```
docker-compose up -d
```

<p>Above docker command will pull the image, create, run and start the Docker Container / Streaming Server already configured with ports opened.</p>


<h2>Attach to the Running RTMP Docker Container</h2>

```
docker attach nginx-rtmp-server
```

<h2>To Update the server packages on the NGINX / RTMP Docker Container</h2>

```
./update
```

<h2>Edit and Add your Stream Key and URL's & Set your RTMP Servers Stream Key to the RTMP Config</h2>
<p>Stream URL / Key from Restream.io, Youtube, Twitch</p>
<p>(Example: - Change -> push rtmp://live.restream.io/streamkey;)</p>
<p>SETTING RTMP SERVERS STREAM KEY  (Can be named anything, No spaces.)</h2>
<p>(EXAMPLE: Change -> rtmp://127.0.0.1/live/YOURSTREAMKEY to rtmp://127.0.0.1/live/ANY-KEYNAME-YOU-WANT)</p>

```
./edit-rtmp
```

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

<p>Your docker streaming server is now started and running in the background...</p>
<p>You can now connect to it, using your preferred streaming software. (obs studio, xsplit, vmix, streamlabs obs, etc)</p>

<h1>Setting up main gaming computer to stream to NGINX / RTMP</h1>
<p>Any ol Gaming PC with OBS Studio & NVENC encoding.</p>
<p>In OBS, i use NVENC encoding and I use my monitor’s native resolution (1080p).</p> 
<p>Using OBS Studio, in your broadcast settings you need to use the “Custom” streaming service.</p>
<a href=""><img src="https://m1-gamingz.com/wp-content/uploads/2021/03/Screenshot-2021-03-27-130647-live.png" alt="M1GC">
</a>

<p>The Streaming URL will be something like rtmp://192.168.1.100/live (Use your own server’s IP).</p>
<p>Your Stream Key needs to be the same you used in your nginx configuration. </p>
<p>(Example: KEYNAME-YOU-SET)</p>

<p>In the Encoding, use <a href="https://www.nvidia.com/en-us/geforce/guides/broadcasting-guide/" target="_blank">NVIDIA NVENC</a> (Since it doesn’t use a lot of CPU).</p>

<h3>Bit-rates</h3>

<p>Click <a href="https://support.google.com/youtube/answer/2853702?hl=en" target="_blank"> here</a> for Live encoder best settings for bit-rates, and resolutions</p>
<p>You may need to reduce your bit-rate depending on services bandwidth limits.</p>
<p>You may need to adjust your max bit rate according to your needs and capabilities</p>

<h3>AUDIO</h3>

<p>As for Audio encoding, I use the AAC codec, 160 bit rate and a Format of 44 or 48 Khz.</p>

* RTMP Video on demand FLV/MP4, playing from local filesystem or HTTP
* Stream relay support for distributed streaming: push & pull models
* Recording streams in multiple FLVs
* H264/AAC support
* Online transcoding with FFmpeg
* HTTP callbacks (publish/play/record/update etc)
* Running external programs on certain events (exec)
* HTTP control module for recording audio/video and dropping clients
* Advanced buffering techniques to keep memory allocations at a minimum level for faster streaming and low memory footprint
* Proved to work with Wirecast, FMS, Wowza, JWPlayer, FlowPlayer, StrobeMediaPlayback, ffmpeg, avconv, rtmpdump, flvstreamer and many more
* Statistics in XML/XSL in machine- & human- readable form

ENJOY! 
