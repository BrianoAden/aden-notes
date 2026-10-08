---
title: Routing USB on PCB
publish: "true"
---
File Created: 2026-01-07 19:30  
Last Modified: 2026-01-07 19:30  

Hello! On this page, I will discuss all of the things necessary to successfully route your [[UniversalSerialBus|USB]] port to some receiving device on any PCB you might design. The board being designed, and the one that will be referenced throughout this page, is a test board for the RFD900x 900 MHz radios.  

# USB Port  

Below is a photo of a USB-A port symbol in KiCad.  

![[file-20260107193349806.png]]  

The `VBUS` line is our +5V line, which we can use to power any connected device. The `D+` and `D-` are our data lines, of which they are a [[DifferentialSignaling|differential pair]]. `GND` is our ground line, of course. The `Shield` line is directly connected to the devices metal casing, which acts as a shield for [[ElectromagneticInterference|EMI]]/[[ElectrostaticDischarge|ESD]], and should be shorted to ground to drain out any noise or interference.  

Below is a photo of a micro-USB type B port symbol in KiCad. The cables used with the board referenced on this page are USB-A to micro-USB.  

![[file-20260107194352052.png]]  

Note that the only difference is the `ID` line, or Identification line. Tie it to ground if your device is a Host device, and leave it floating if it is a peripheral. We are going to leave it floating, as we have no need to control peripheral devices, such as mice or keyboards.   

# Signal Isolation  

For this PCB, I am going to include circuits to isolate both the power and data lines, since it will be directly connecting to the user's personal computer, and the last thing I want is to be blamed for frying somebody's motherboard. The only thing that truly requires isolation are the data lines, though, since ideally our RFD900x radios would be powered elsewhere and not by the finicky +5V from our laptop USB ports. However, on the off-chance that we find ourselves wanting to test using power from our laptops, I will include the `VBUS` isolation.  

To isolate `VBUS`, we are going to use the [NXE2S0505MC](https://pim.murata.com/en-us/pim/details/?partNum=NXE2S0505MC), 


# References

[How to Route USB Data Lines on PCB](https://www.youtube.com/watch?v=Itsrdc8tX7M)  
[Isolated USB Connection Project](https://resources.altium.com/p/isolated-usb-connection-project)