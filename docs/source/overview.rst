Overview
=========

(TODO: insert a nice schematic)

What one can do with the system
--------------------------------

In principle, this system turns the `Raspberry Pi 4`_ and a `Pi NoIR camera`_ into
a webcam surveillance system, by:

* setting up a webcam in your local area network (LAN).
* controlling the acquisition from the web browser:

  * watching the captured videos in real-time.
  * turning on/off the infrared (IR) lights attached to the camera.
  * adjusting the angle of the camera online.

Hardware components
--------------------

`Raspberry Pi 4`_
^^^^^^^^^^^^^^^^^^

.. image:: /resource/pi4.jpg
   :scale: 30 %
   :alt:   Raspberry Pi 4

Connected to the LAN via Ethernet (wired) or via the Wi-Fi.

`Pi NoIR camera`_
^^^^^^^^^^^^^^^^^^

.. image:: /resource/noirv2.jpg
   :scale: 45 %
   :alt:   Pi NoIR camera

Connected to the Raspberry Pi through a CSI ribbon cable.

IR lights
^^^^^^^^^^

.. image:: /resource/IRlights.jpg
   :scale: 25 %
   :alt:   a set of IR lights for Pi NoIR camera

Assumes to be something similar to the image above, but anything will do in principle.

Pan/tilt unit
^^^^^^^^^^^^^^

.. image:: /resource/pantilt.jpg
   :scale: 50 %
   :alt:   a pan-tilt unit

This unit is used to change the capture angle of the camera.
Refer to `this video about how it is made up <https://www.youtube.com/watch?v=4A7tJ0QH4L4>`_,
or watch `this video to see how it works <https://www.youtube.com/watch?v=a0GSw3zhckU>`_.

But again, the shape can be anything as long as it is made from a pair of servo motors
which is controlled using the PWM.

Software components
--------------------

We are going to set up two local web services, namely:

`mjpg-streamer`_
^^^^^^^^^^^^^^^^^

This is an open software for web-streaming the video from USB cameras
using the Motion-JPEG format.

In particular, we are going to use the version which the CSI-connection RasPi cameras
can be used as the source.

camera-control
^^^^^^^^^^^^^^^

This is a custom Python library to control the IR lights and the servo motors.
Under the hood, the library is made from a set of Python scripts based on the `pigpio`_
library to control the IO pins of the Raspberry Pi.
We turn the scripts into a web service by means of the `Flask`_ Python libary.

In addition to the services above, we use an HTTP server program called `Nginx`_.
Using this has an advantage of being able to seamlessly access to these local
services without remembering about how we have set them up.


.. _Raspberry Pi 4: https://www.raspberrypi.com/products/raspberry-pi-4-model-b/
.. _Pi NoIR camera: https://www.raspberrypi.com/products/pi-noir-camera-v2/
.. _mjpg-streamer: https://github.com/jacksonliam/mjpg-streamer
.. _pigpio: http://abyz.me.uk/rpi/pigpio/python.html
.. _Flask: https://flask.palletsprojects.com/
.. _Nginx: https://nginx.org/en/
