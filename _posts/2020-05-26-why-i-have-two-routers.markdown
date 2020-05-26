---
layout: post
title:  "Why I Have Two Routers"
date:   2020-05-26
categories: datacenter
---

I currently have two routers on my network for one internet connection.
* Netgear Nighthawk  X8 AC5300 (main)
* Dell R210 running pfSense (secondary)

![network-diagram](/assets/images/network-diagram-2020-5-26.png)

#### Netgear Nighthawk X8
Let's start with the Nighthawk because that is the backbone of the entire operation. It has great wireless, but does not offer a lot of configuration.

Pros:
* Excellent Wireless Range
* Simplicity
* Easy Setup
* 6 ethernet ports
* DMZ Support (This will become useful later)

Cons:
* Limited Configuration
* Very Poor Cooling (Very hot too touch and I think it has shut itself off because of overheating before)
* Slower Performance
* Dated Web Interface
* No VLAN support from Layer 3 switching

#### Dell R210 running pfSense
This is the router behind the Nighthawk and running my entire data center operation.

Pros:
* Very fast
* Many more configuration options
* Fast/Updated Web Interface
* Built in OpenVPN support
* VLAN Support
* Layer 3 switching
* Dual WAN Support
* More/Better DNS Options
* Multiple Dynamic DNS Options
* Plugins

Cons:
* More Difficult Setup
* More Complex to Manage
* No Built-in Wireless
* Only 2 ethernet ports (Unless you add more)

#### Why?
I generally live about three hours away from my data center while I am at school. If the pfSense box was the only device running the network, and it were to go down, I would need to travel home to fix it quickly. My family obviously needs internet and I can not travel home at a moments notice. So when the pfSense box and data center go down the house stays up. This also gives me my own private network to play on without interrupting the house. I use to have to restart it often with other routers when people were using the internet and people were not pleased. For some reason almost every consumer router I have used requires a restart for basic changes.

#### How?
It took a bit of thinking but I finally finalized the configuration during my Covid-19 isolation time. The Nighthawk actually supports a DMZ which makes my life easier. So I basically put the pfSense box on a static IP address and opened the DMZ on the Nighthawk to it. So really it is like my pfSense box is on the front of the network. It also keeps any data center operations separate from my family network traffic.

Having it this way also allows me to open ports when needed which required a restart on the Nighthawk, thus knocking everyone off the internet at home.

I now have a VPN tunnel setup to remote into the data center network either on the Nighthawk connection or outside of the house.
