<h1>NGINX-based Media Streaming Server / RTMP / FFMPEG SERVER</h1>
https://hub.docker.com/r/murderousone/nginx-ffmpeg-rtmp
</hr>
<h3>PLEASE NOTE: I LIKE TO DO THINGS WITH DOCKER MANUALLY <br></h3>
</h2>SO THESE WILL CONTAIN SCRIPTS TO MAKE LIFE EASIER</h2>
<p>THIS DOCKER IMAGE WILL WORK WITH 64 Bit Systems.</br>
<b>DOCKER IMAGE MAY NOT WORK WITH  32bit Systems.</b></br>
<p>Image can be attached too and is fully customizable.</p>
<p>Image has simple pre-installed bash scripts to make running the server easier.</p>

<h1>NGINX-based Media Streaming Server</h1>
<h2><p>Based on Ubuntu Server Latest 64 Bit </p></h2>
<h2><p>Based on Debian Server Latest 64 Bit </p></h2>
</br>
<h3>UPDATES FOR UBUNTU SERVER LATEST</h3>
* Updated NGINX to the Latest Version - NGINX v1.19.7</br>
* COMPILED WITH NGINX RTMP MODULE</br>
* EASY INIT SCRIPT FOR NGINX START, RESTART, STOP</br>
* EASY SHELL EXACUTABLE SCRIPTS FOR EDITING, NGINX START, RESTART, STOP AND EASIER MANAGING YOUR RTMP SERVER</br>
* FFMPEG LATEST STABLE VERSION</br>
* ALL UBUNTU PACKAGES UPDATED</br>
</hr>
<h3>UPDATES FOR DEBIAN SERVER LATEST</h3>
* Updated NGINX to the Latest Version - NGINX v1.19.7</br>
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
<h1> DOWNLOAD NGINX-based Media Streaming Server Docker Image, Update, & Run Your own RTMP Streaming DOCKER Container</h1>

<h2>Pull the NGINX-based Media Streaming Server Docker Image from our Git / Docker Server Registry (Ubuntu Server Latest | Debian Server Latest)</h2>

```
docker pull murderousone/nginx-ffmpeg-rtmp:ubuntu-latest
```

<h2>FOR DEBIAN</h2>

```
docker pull murderousone/nginx-ffmpeg-rtmp:debian-latest
```

<h2>Run / Start the RTMP Docker Container (UBUNTU)</h2>

```
docker run -itd -p yourhostip:80:80 -p yourhostip:443:443 -p yourhostip:1935:1935 -h yourhostname --name nginx-rtmp-server murderousone/nginx-ffmpeg-rtmp:ubuntu-latest /bin/bash
```
<h2>Run / Start the RTMP Docker Container (DEBIAN)</h2>

```
docker run -itd -p yourhostip:80:80 -p yourhostip:443:443 -p yourhostip:1935:1935 -h yourhostname --name nginx-rtmp-server murderousone/nginx-ffmpeg-rtmp:debian-latest /bin/bash
```
<h2>Attach to the Running RTMP Docker Container </h2>

```
docker attach nginx-rtmp-server
```

<h2>Update Packages on the RTMP Docker Container</h2>

```
./update
```

<h2>Edit and Add your Stream Key and URL's to the RTMP Config</h2>


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

<h1>SCRIPTS CAN BE EXECUTED WITHOUT ATTACHING</h1>
<h3>EXECUTE THE START/STOP/RESTART/UPDATE  SCRIPTS FROM OUTSIDE THE CONTAINER WHILE ITS RUNNING</h3>


<h2>START THE RTMP SERVER</h2>

```

docker exec -it nginx-rtmp-server ./start-rtmp
```

<h2>STOP THE RTMP SERVER</h2>

```
docker exec -it nginx-rtmp-server ./stop-rtmp
```

<h2>RESTART THE RTMP SERVER</h2>

```
docker exec -it nginx-rtmp-server ./restart-rtmp
```

<h2>UPDATE THE RTMP SERVER</h2>

```
docker exec -it nginx-rtmp-server ./update
```

</hr>

<h1>CHECK, START, STOP, DELETING, DOCKER CONTAINERS / IMAGES</h1>

<h2>CHECK RUNNING DOCKER CONTAINERS INFO</h2>

```
docker ps -a
```

<h2>CHECK DOCKER IMAGES</h2>

```
docker images
```

<h2>START THE RTMP SERVER  DOCKER CONTAINER</h2>

```
docker start nginx-rtmp-server
```

<h2>STOP THE RTMP SERVER DOCKER CONTAINER</h2>

```
docker stop nginx-rtmp-server
```

<h2>DELETE THE RTMP SERVER DOCKER CONTAINER</h2>
<h5> container must be stopped to delete</h5>

```
docker rm nginx-rtmp-server
```

<h2>DELETE A DOCKER IMAGE </h2>
<h5> <p> Docker images must not have a container using it's image to delete. </h5> </p></br>
<h5> <p>Stop & Delete any created containers that may use the image before attempting to delete a image</p></h5>

```
docker rmi murderousone/nginx-ffmpeg-rtmp:ubuntu-latest
```

<h2>FOR DEBIAN</h2>

```
docker rmi murderousone/nginx-ffmpeg-rtmp:debian-latest
```

</hr>
<h1>USE OBS STUDIO TO CONNECT / LIVESTREAM</h1>
<p>The Streaming URL will be something like rtmp://yourserverslocalipaddress/live (Use your own servers local IP address).</p>
<p><b>STREAM URL:</b> rtmp://localhost/live or rtmp://yourserverip/live</p></br>
<p><b>STREAMKEY:</b></p>
<p><b>Your Stream Key needs to be the same you used in your nginx configuration or Enter anything as a stream key if not in nginx config.</b></p>
<p><b>STREAM KEY EXAMPLE: rtmp://localhost/live/<b>yourstreamkey</b> in nginx config (./edit-rtmp)</b></p>
<h2><strong>Setting up the main broadcasting computer</strong><br></h2>
Main gaming computer or Any ol Gaming PC Capable of running&nbsp;OBS Studio with x264 or&nbsp;NVENC encoding.
</p>

<p>
	In OBS, i use NVENC encoding and I use my monitor&rsquo;s native resolution (1080p).&nbsp;
</p>

<p>
	Using OBS Studio, in your broadcast settings you need to use the &ldquo;Custom&rdquo; streaming service.
</p>

<p>
	<a  href="https://m1gc.m1-gamingz.com/topic/12736-private-nginxrtmp-server-live-streaming-using-docker/" rel="external nofollow" role="link" tabindex="0" target="_blank"><img alt="OBS Tutorial" src="https://www.dacast.com/wp-content/uploads/2015/10/Custom-Streaming-Server-in-OBS.png" style="width: 815px; height: 647.181px; margin: 0px;" width="981"></a>
</p>
<p>
	In the Encoding, use <a href="https://www.nvidia.com/en-us/geforce/guides/broadcasting-guide/" rel="external nofollow">Nvidia NVENC</a> (Since it doesn&rsquo;t use a lot of CPU. If you do not have the option, Try x264 on VeryFast or Faster).
</p>
<p>
	<span style="color:#2ecc71;"><strong>Bitrates</strong></span><br>
	Click&nbsp;<a href="http://bit.ly/2InCifU" rel="external nofollow" target="_blank">here</a> for Live encoder settings, bitrates, and resolutions
</p>
<p>
	You may need to reduce your bitrate depending on&nbsp;services bandwidth&nbsp;limits.<br>
	You may need to adjust your max bitrate according&nbsp;to your needs and capabilities
</p>
<p>
	<span style="color:#2ecc71;"><strong>Audio</strong></span><br>
	As for Audio encoding, I use the AAC codec, 96k bit rate and a Format of 44 or 48Khz.<br>
	<br>
	<span style="color:#c0392b;">That&#39;s it</span>You can now stream direct with your own private rtmp server.
</p>

