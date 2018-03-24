# Chapter 4 Network Layer
### Intro
- internet’s network layer is best effort service model
  - Internet doesn't provide any service
  - some service you could provide:
    - guaranteed delivery w/ guaranteed delay
    - order persistence
    - etc
- There are alternatives like ATM

Three most important features in this layer
1. Routing
2. Forwarding
3. Connection setup (not internet)

### connection setup
only for some architectures (not internet)\
VirtualCircuit (VC) vs datagram\

### Routers
  - input ports
    - line termination
    - link layer protocol
    - lookup, forwarding, queing
  - Switching fabrics
    - via memory (I)
    - via bus (II)
    - crossbar (III)
  - output ports
    - buffer
    - link layer protocol
    - line termination

#### Delays in routers
  Buffer size for output is to have RTT x C\
  Recent study suggests RTTxC/sqrt(N)\
  input buffer is needed for HeadOfLine delay

### Datagrams
  please review the picture with the values\
  header length = usually 20bytes\
  fragment offset = multiple of 8 bytes\
  Fragmentation

### IPv4
  subnet /24subnet could have 255(end hosts) + 1 (for router) connections\
  Classless InterDomain Routing (CIDR) supports arbitrary number of bits as the subnet mask\
  255.255.255.255 is a special broadcasting IP

#### DHCP
  - Dynamic Host Configuration Protocol
  - not only IP but also default gateway, local DNS server, subnet mask
  - pnp protocol
  - 4 steps process
  - cannot maintain TCP connection between changes 

  1. *DHCP server discovery* - UDP(67) with 255.255.255.255(broadcast) from 0.0.0.0(this host)
  2. *DHCP server offer* - you might get multiple offers, DHCP server will broadcast this offer
  3. *DHCP request* - choose one offer then broadcast with the server ID 
  4. *DHCP ACK* - server acknowledge, good to use this ip

#### NAT
  - Network Address Translation
  - keep track of things through NAT table
  - Some issues
    - How to host a server behind NAT
      - port forwarding (manual and static)
      - UPnP (automatic and dynamic)
      - relaying
    - controversy: NAT violates layer3, IPv6 to solve this problem

#### ICMP
  - Internet Control Message Protocol
  - `traceroute` and `ping`

#### IPv6
  - 128bits addr instead of 32
  - 40bytes header (16 + 16 for addresses + 8 for version, flowlabel, length, next hdr(like TCP or UDP) )
  - nomore Checksum, options, fragmentation
  - comes with ICMPv6
  - Transition from v4
    - dual stack routers
    - tunneling


