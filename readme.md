# WeDioV2

  

### ICE CANDIDATES
  

> ICE (Interactive Connectivity Establishment) candidates are a key component of the WebRTC (Web Real-Time Communications) protocol used for establishing real-time communication between web browsers.

When two devices want to establish a connection, each device needs to determine its own network address, i.e., IP address and port number, so that the other device can send data to it. ICE candidates are a list of possible network addresses that a device can use to establish a connection.

  

ICE candidates are typically gathered by the device using STUN (Session Traversal Utilities for NAT) and TURN (Traversal Using Relay NAT) servers. STUN servers help the device discover its public IP address and port, while TURN servers relay traffic if a direct connection between the devices cannot be established due to NAT (Network Address Translation) or firewall issues.

Once each device has gathered its list of ICE candidates, they exchange these candidates with each other until they find a mutually agreeable candidate that allows them to establish a direct connection.


### STUN SERVER

>A STUN (Session Traversal Utilities for NAT) server is a type of server used to help devices discover their public IP address and port when they are behind a NAT (Network Address Translation) router.

When a device is connected to a private network, its local IP address and port are not visible to the outside world. Instead, the NAT router assigns a public IP address and port to the device for communication with the internet.

The problem is that the device needs to know its public IP address and port in order to receive incoming data from other devices. This is where the STUN server comes in.

The STUN server acts as an intermediary between the device and the internet. When the device sends a request to the STUN server, the server replies with the device's public IP address and port. The device can then use this information to communicate with other devices on the internet.

For example, imagine you are using a video conferencing app on your computer behind a NAT router. The app will use a STUN server to discover your public IP address and port, which it will then use to establish a connection with the other person's computer. Without the STUN server, the app would not be able to establish a connection because it would not know your public IP address and port.

In summary, a STUN server helps devices behind a NAT router discover their public IP address and port so they can communicate with other devices on the internet.

### What is a NAT ?

A router alters a local IP address to be available publicly using a technique called NAT (Network Address Translation).

When a device is connected to a local network, it is assigned a private IP address by the router. This IP address is only visible within the local network and cannot be used for communication with devices outside the network.

To enable communication with devices outside the network, the router assigns a public IP address to the network as a whole. The router then uses NAT to map each private IP address in the local network to the public IP address assigned to the router.

When a device on the local network sends a request to the internet, the router replaces the source IP address in the request with its own public IP address. This makes it appear as if the request is coming from the router itself rather than the device behind it.

When the response is sent back to the router's public IP address, the router uses NAT to forward the response to the appropriate device on the local network based on the destination IP address in the response.

In this way, the router allows devices on the local network to communicate with devices on the internet using a single public IP address, while also keeping the private IP addresses of the devices hidden from the outside world.

Overall, the process of NAT allows a router to alter a local IP address to be available publicly by mapping each private IP address to a public IP address and translating requests and responses between the two.

## FAQs

#### Is every router behind a NAT?
Yes.

I means it’s impossible to be certain that every single home internet router ever sold has NAT but….yes.

It’s inherent in their design. Bear in mind that a home ADSL “router” is not a router in the classical OSI 7 Layer model. It’s actually several devices (a modem. router and switch) plus a bunch of software including the NAT, firewall, DHCP server etc etc.

What home users want is a network for their devices and access to the internet on the other side of the router. You only get one IP usually from your ISP yet you have multiple devices on your LAN and they'll need at least one IP too and to be able to communicate with each other. A NAT is the way to do this.

NAT is Network Address Translation. The NAT take say a web request from a PC on the LAN and sends it to the web server but alters it (translates it) so that the return address is the address of the router not the PC. Why? Because the IP address of the PC is only valid on the local home network and, as previously mentioned, you only have one public-facing IP that your ISP gives you. Sending it with the local IP address would not allow the webserver response to find your PC. When the reply is received from the web server the NAT then sends it to the relevant PC. There is no other simple way of doing this with IPv4. One way or another you have to be able to share a single public IP address amongst multiple devices.

IPv6 could solve this however since it can give every single device in the world a unique IP address and leave LOADS of addresses to spare.


#### Why and How does NAT convert private IP to public IP ? 

In the IPV4 addressing there are only 2 power 32 addresses. Which means multiple devices will have repeated IP addresses. So each router is give a unique IP address that eliminates the need for each device having a unique address.

The router has an address which is the public address of the entire network.

The router assigns a private IP to all of the devices in the network. These private IPs are hidden to the outside world. 

Only the router with the help of a NAT table has access to these private IPs. 

When a request is sent, the NAT resolves the private IP of the device into the public IP, and records this IP as the source of the network request.

Vice versa is also true. 

So the router acts as a medium of communication for the rest of the internet to interact with this local network.