+++
title = 'Going Crazy and Buildimg a Homelab in my Dorm'
date = '2026-04-28T02:23:42-05:00'
draft = true
+++
## Why?

I've had a small homelab, mainly of older desktops and workstations for a while now, but I have always dreamed of creating a high availability setup for my lab. I've also always wanted to try out ceph and high speed networking in a cluster. That let me down a rabbit hole recently with the Mellanox SX6036, an inexpensive 36-port Infiband switch that can also do regular old ethernet at up to 56Gbe with the right cards and cables. I thought why not? What could go wrong? So I bought one. It did take quite a bit of work to setup but I enjoyed playing around with it to the point I decided to also pull the trigger on some conpute.

## The Compute

Around last autumn I saw what was starting to happen to ram pricing and decided to pull the trigger sooner than later so I aquired three Cisco C220 M5s which have been pretty nice if I'm being honest. they are 1U dual cpu servers based on Cascade Lake. I bought them with:

- 2x Intel Xeon 4216 (16C, 32T per cpu)
- 2x DDR4-2933 Registered ECC 32GB modules
- 2x 700W PSU

Overall I felt quite satisfied with this purchase and it has allowed me to do some pretty fun experiments on the cluster. I also needed some storage so apart from some pretty standard boot drives each node has a high endurance 3.84TB SAS SSD, so a total of 3 OSD.

## Overall Gear

- 3x Cisco C220 M5
- 2x Mellanox SX6036 Switches
- 6x ConnectX-3 Pro
- Lots of Cables
- Unifi Fiber Gateway

## This is where things start to get complicated. after eating up a cluster with one switch I decided to order another to do MLAG. for those unfamiliar MLAG is a form of multichassis link aggregation. essentially each client connects to both switches so if a switch fails the aggregated link stays up. in this case it support 802.11 lacp group.