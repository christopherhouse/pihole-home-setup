# Home Network PiHole Configuration
This is the docker compose yaml I use to manage PiHole contianers on my home network.  The network has four VLANs:

|VLAN|Purpose|
:-----|:--------
|Trusted|Personal devices for my wife and I|
|Untrusted|IoT Devices (Echo, TV, etc)
|Work|Company issued devices|
|Guests|For people visiting our house|

## Previous Setup
Prior to moving to this configuration, I had two PiHole instances running in my Trusted vlan, then opened firewall ports to allow DNS requests from all other VLANs into my trusted network.

## Current Setup
My current setup adds VLAN specific interfaces to my Raspberry Pi for each of my VLANs.  I'm now running two PiHole containers on each VLAN, for primary and secondary DNS.  This removes the need to open any firewall ports into my Trusted VLAN.

### VLAN Interfaces

## Future
While this was a fun exercise, spinning up 8 PiHole containers on a single Pi, it does put all my DNS eggs in one basket.  I'll eventually split this into two docker compose files so that I can run one PiHole per network on one Pi and another instance for each network on a separate Pi so I have some hardware redundancy.