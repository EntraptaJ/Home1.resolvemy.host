# sbc1.home1.resolvemy.host

Rock Pi E without any HATs plugged into the wall near our WAN termination modem from Oxio, we have 1000M down 100M up.

This is acting as a Router, Wireguard Tunnel Host, the only LAN wired connection to the Apartment/Personal Network/Eero/Home/LAN, Compute node for IoT software


It's currently running the following containers, YES CONTAINERS, currently its running with Docker Compose however I plan to get this running Kubelet/ContainerD and running in the home1.resolvemy.host cluster

# Containers

## HomeAssistant

## Zigbee2MQTT
This is using [Slaesh's Zigbee Dongle](https://slae.sh/projects/cc2652/) which is passed through to the container

## Mosquitto

This was rather lazily thrown togehter, doesn't use auth, and etc etc its a nightmare and security risk that I intend and plan on moving away from but I didn't have the spoons when I set this up and just wanted my damn Zigbee lights to work


## Wireguard Stuff

This node is currently not port forwarded/exposed to the internet but it is in my TODO list, right now I connect to it from my windows computer, phone, and iPad to gain access to my Kubernetes cluster locally and access the management systems in dc1.resolvemy.host using the GRE tunnel to wan-gw1.dc1.resolvemy.host



# BGP Peering

Currently we peer with

nuc1.home1.resolvemy.host - 172.31.241.253
wan-sw1.dc1.resolvemy.host - 172.31.241.2

sbc1.home1.resolvemy.host doesn't have a public address but is setup connected with ethernet to ap1.home1.resolvemy.host which has port forwarding port 1723



# Networking

The Rock Pi E has wifi chip and 2 Ethernet ports, we have the 1G port connected directly via a short ethernet cable to ap1.home1.resolvemy.host which is a [Eero 6 Wifi AP]() provided by Oxio, the ethernet port acts as a switch for the LAN network accessed over Wifi



We have the it connecting over Wifi as well for a fallover network path in the event of a failure of the ethernet cable but wifi is still operational, this will be handy for high availability as it means we will still have access to all our IoT and smart light system even in the event of needing to move our NUC or whatever, (TODO: Setup a DIY power bank powering the sbc1.home1.resolvemy.host and ap1.home1.resolvemy.host over USB-C should only be like $50 worth of parts to get us a few days of internet maybe if theres a power outage but the ISP gear still works? Should test this)

