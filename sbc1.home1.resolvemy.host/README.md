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

The Rock Pi E has 