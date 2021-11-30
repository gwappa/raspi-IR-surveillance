Software setup
===============

Using the automation shell script should help...

#. apt-get update
#. setup mjpg-streamer:
    #. apt-get install cmake libjpeg8-dev
    #. clone mjpg-streamer & install
    #. (copy) mjpg-streamer service setup

#. setup camera-control:
    #. apt-get install python3 pigpio (in case)
    #. pip3 install flask
    #. install camera-control (probably in the repo)
    #. (copy) camera-control service setup

#. setup nginx:
    #. apt-get install nginx
    #. rewrite nginx config

#. init.d and systemd setup:
    #. enable nginx, camera-control and mjpg-streamer services
    #. activate the services
