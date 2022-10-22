# Unifi-controller

This Dockerfile builds an image to run the latest Unifi Controller software, same as availible for cloudkey or dreammachine.

## Build

    docker build -t unifi .

## RUN
    docker run -d \
               --init \
               --mount type=volume,source=unifi_config,target=/config \
               -p 3478:3478/udp \   # STUN
               -p 6789:6789 \       # Unifi mobile speed test
               -p 8080:8080 \       # Device & controller communication
               -p 8443:8443 \       # Controller Web GUI
               -p 8843:8843 \       # HTTPS portal redirection
               -p 8880:8880 \       # HTTP portal redirection
               -p 10001:10001/udp \ # Device discovery
               --name unifi_run \
               unifi