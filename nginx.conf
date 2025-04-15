#########################################################################
### NGNIX CONF FOR DOCKER RTMP FFMPEG STREAMING SERVER ##################
#########################################################################
### CUSTOM NGINX CONFIG USED IN DOCKER CONTAINER FOR FFMPEG STREAMING ###
#########################################################################

worker_processes auto;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;
    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;

        location / {
            root   html;
            index  index.html index.html;
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }
}
#    ____ _____ __  __ ____    __  __ _____ ____ ___    _      ____ _____ ____  _____    _    __  __ ___ _   _  ____   ____  _____ ______     _______ ____
#   |  _ \_   _|  \/  |  _ \  |  \/  | ____|  _ \_ _|  / \    / ___|_   _|  _ \| ____|  / \  |  \/  |_ _| \ | |/ ___| / ___|| ____|  _ \ \   / / ____|  _ \
#   | |_) || | | |\/| | |_) | | |\/| |  _| | | | | |  / _ \   \___ \ | | | |_) |  _|   / _ \ | |\/| || ||  \| | |  _  \___ \|  _| | |_) \ \ / /|  _| | |_) |
#   |  _ < | | | |  | |  __/  | |  | | |___| |_| | | / ___ \   ___) || | |  _ <| |___ / ___ \| |  | || || |\  | |_| |  ___) | |___|  _ < \ V / | |___|  _ <
#   |_| \_\|_| |_|  |_|_|     |_|  |_|_____|____/___/_/   \_\ |____/ |_| |_| \_\_____/_/   \_\_|  |_|___|_| \_|\____| |____/|_____|_| \_\ \_/  |_____|_| \_\
#
rtmp_auto_push on;
rtmp {
    server {
        listen 1935;
        ping 30s;
        notify_method get;

        application live {
            live on;

	#PUSH TO PLATFORMS USING FFMPEG x265


#FFMPEG TO TRANSCODE / CONVERT TO 720p

exec ffmpeg -threads 12 -re -i "rtmp://127.0.0.1/live/YOUROBSSTREAMKEY" -c:v libx264 -pix_fmt nv12 -x264-params "nal-hrd=cbr" -vf scale=1280:720 -vb 6000k -minrate 6000k -maxrate 6000k -bufsize 6000k -preset veryfast -q 0 -g 60 -keyint_min 60 -x264opts "keyint=120:min-keyint=120:no-scenecut" -c:a aac -b:a 128k -c:v:a copy -f flv "rtmp://127.0.0.1/liveout/YOUROBSSTREAMKEY";

#SEND STREAM DIRECT

        #PUSH TO RESTREAM.IO
        push rtmp://live.restream.io/live/YOURSTREAMKEY;

	}

	# TRANSCODED 720P Stream #		

	application liveout {
        live on;

	#PUSH STREAM TO STUNNEL FOR FACEBOOK ENCRYPTION --> REQUIRES STUNNEL
	push rtmp://YOURSTUNNELIP:STUNNELPORT/rtmp/YOURFBSTREAMKEY;

	#PUSH TO TROVO
	
	push rtmp://livepush.trovo.live/live/YOURSTREAMKEY;

	#PUSH TO TWITCH
	push rtmp://jfk.contribute.live-video.net/app/YOURSTREAMKEY;
	
	#PUSH TO STEAM
	push rtmp://ingest-rtmp.broadcast.steamcontent.com:1935/app/YOURSTREAMKEY;

	#PUSH TO KICK --> REQUIRED STUNNEL
	push rtmp://YOURSTUNNELIP:STUNNELPORT/rtmp/YOURSTREAMKEY;

	#PUSH TO INSTAGRAM
    push rtmp://YOURSTUNNELIP:STUNNELPORT/rtmp/YOURSTREAMKEY;
            
		}
	}
}
