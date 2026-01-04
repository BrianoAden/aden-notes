---
publish: "true"
---
# RFD900x Documentation

2025-10-02 17:41

Status:

Tags: [[Robotics]]

## What Are The RFD900x Radios?

The RFD900x Radios are 900M

## What Are we Going to do with the RFD900x Radios?

We are going to use them to setup our 900Mhz tlm + cmd RF link! They are typically used for this purpose on drones or similar applications, typically paired with a flight controller (like the Pixhawk) to packetize data according to the MAVLink protocol. HOWEVER, we can do all of this with our regular degular computers or onboard NVIDIA Jetson.

## What we Currently Need to Figure Out

How we're going to use the MAVLink protocol to communicate to the RFD900x **PyMavlink**

Pinout of RFD900x

![[Pasted image 20251002175510.png]]


Reddit post regarding flashing red LED on RFD900x modules when they are connected. Should be okay!
![[Pasted image 20251007170158.png]]

![[Pasted image 20251007171041.png]]


## What We Need to do With These Radios

We need to:
1. Put together a quick power supply system for the two modems. 
	1. Probably just hook the power supply up to breadboard rails and use that. 
	2. (Insert picture of power supply system here)
2. Test NLOS effective distance
3. Figure out how to configure microcontrollers to communicate over the RF Link
	1. First thing to do is find a second USB to TTL cable. If we can't find one, we're fucked. 
		1. When we do find one, connect both modems to a computer and see what data is being transmitted and received.
	2. Look at Rocky's code. 

Things to note: 

It is okay to power RFD900x off computer if you are only configuring the devices using RFDTools (a Windows only application). If you are transmitting or receiving data, you will need to power the devices using a power supply. This is because the devices can draw up to 1A of current and cause brownouts. 

Power Supply settings: 5V 1A



# References
https://ardupilot.org/copter/docs/common-rfd900.html