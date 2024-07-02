# Network+ Notes


NAS(Network Attached Storage): File level access. If you want to make a change in a file you need to overwrite the whole file.

SAN(Storage Area Network): Block level access. Looks and feels like your local file system.

Demarcation point: The point where you connect with the outside world.
- Usually a box.

Network function virtualization(NFV): Replace physical network devices with virtual network devices.

VLAN(Virtual Local Area Network): Local group of devices that are configured to communicate with each other but they are not connected to the same physical network devices since they are segmented.

Satellite networking:
- High latency.
- Expensive compare to terrestrial networking.

Cable broadband: Transmission across multiple frequencies.

Subnet mask: Used by the local device to determine which subnet it is on.

Default gateway: The IP address of the router in your subnet.

Loopback address: Ranges from 127.0.0.1 -> 127.255.255.254

Virtual IP addresses(VIP): Not associated with a physical network adapter, typically used for virtual machines.

NAT(Network Address Translation): Translates a private IP into a public IP usually done by a router when communicating with the internet.

Private IP addresses ranges:
- 10.0.0.0 - 10.255.255.255 Class A
- 172.16.0.0 - 172.31.255.255 Class B
- 192.168.0.0 - 192.168.255.255 Class C

Unicast: One-to-one communication between two devices.

Broadcast: One-to-all communications.
- Routing updates.
- ARP requests.

Multicast: One-to-many.

Anycast: One-to-one of many.
- Anycast DNS.

DHCP(Dynamic Host Configuration Protocol): A server that assings address and IP configuration for almost all devices automatically.
- DHCP relay: For networks where there is no DHCP the router communicates with the DHCP server in another network to configure their local devices.

Network broadcast address: 255.255.255.255(IP), FFFF.FFFF.FFFF.FFFF(MAC).

A & AAAA: 
- A: IPv4 record.
- AAAA: IPv6 record.

CNAME(Canonical Name Records): Provide an alias for a server that has multiple services running on them. Ex:
- ftp IN CNAME mail.mydomain.com
- www IN CNAME mail.mydomain.com

MX(Mail Exchanger Record): Determines the host name for the mail server.

NS(Name Servers): DNS.

PTR(Pointer Record): Reverse of A & AAAA records, provides a domain for an IP address.

TXT(Text Record): Text information.

NTP(Network Time Protocol): Syncronize time between miltiple devices.

Three-tier architecture:
- Core: Center of the network. Webservers, DB's, and applications.
- Distribution: Midpoint between core and the users. Communication between access switches.
- Access: Where users connect. End stations, printers.

SDN(Software Defined Networking):
- Infrastructure layer: Process network frames and packets.
- Control layer: Routing tbales, session tables NAT tables.
- Application layer: Condifure and mamage the device.

Spine and leaf architecure: Spine -> Leaf -> App servers.
- Advantages:
	- Simple cabling.
	- Redundant.
	- Fast.
- Disavantages:
	- Additional switches add more cost.

SAN(Storage Area Network): 
- Block level access.
- Very efficient reading and writing.
- Requires a lot of bandwidth.

Fibre Channel(FC): High speed topology that connect servers to storage.
- Supports fiber and copper.

Infra as a service(IaaS): You provide OS and app. AWS EC2 instance.

Platform as a service(PaaS): You provide application. Google app engine.

Elasticity: Scale up or down as you need.

VPC endpoint(Virtual Private Cloud): Connects servers over the internet.

SCADA/ICS(Supervisory Control and Data Acquisition System/ Industrial Control System):  Manages equipment; power generation, refining, manufacturing equipment.
- Requieres extensive segmentation, no access from the outside.

Hub: Traffic going in one port is repeated to every other port.

Bridge: Makes forwarding decision in software. Switch betta.

Switch: Makes forwarding decisions based on data link address.

Access point: A wireless router, is a router and an access point in a single device.
- Is a bridge, extendes wired network onto the wireless network.

Cable modem: Connects to broadband network.

DSL modem: Uses telephone lines.

Repeater: Receive signal, regenerate, and resend.

Load balancer: Distribute load between multiple servers.

IDS & IPS(Intrusion Detection System & Intrusion Preventation System): Watch network traffic.
- IPS blocks traffic if it suspects some malicious activity.
- IDS sends alert if it finds something suspicious in the traffic.

Firewall: Filters traffic based on port or application.

Dynamic routing protocols: Listen for subnet information from other routers.
- Sent from router to router.

Routing tables: A list of directions for network packets.
- Time to live: Avoids a packet looping forever.
- Routing protocols: RIPv2, OSPF, EIGRP.

ARP(Address Resolution Protocol): Determines the MAC address based on the IP address.

NDP(Neighbor Discovery Protocol): Replaces ARP from IPv4.
- No broadcasts.
- Automatically configures an IP address without a DHCP server.
	
VLAN trunking: Connects multiple VLAN's.

STP(Spanning Tree Protocol): Prevents loops in layer 2 by identifying interfaces that would create a loop upon connection.

Port mirroring(SPAN): Copy traffic from one interface, used for packet captures.

Ad-hoc: Direct communication between two devices without an intermediary like an access point.

BSSID: MAC address for access points. Access points can share their SSID with other access points.

Wifi auth:
- WPA2 Personal: Everybody uses the same 256 key.
- WPA2 Enterprise: Authentication is done by RADIUS server.
- Open System: No authentication, uses a password.

Cellular networks:
- 2G
	- GSM: Mobile networking standard. Uses SIM cards.
	- CDMA: Each phone call has a code that is to filter each call in the receiving side. Used by Sprint and Verizon.

- 3G
	- Improved speed and connectivity by adding: mobile TV, video on demand, and video conferencing.

- 4G & LTE
	- Converge GSM and CDMA into a single standard(LTE).

- 5G
	- Everything that can be done in a wired network can be done in 5G!.

SNMP(Simple Network Management Protocol): Used to monitor system metrics(Network usage, etc.).

Interface errors:
- Runts: A packer is less than 64 bytes, which may indicated there was a collision.
- Giants: A packet is larger than 1518 bytes.
- GRC error: Failed frame check sequence, it may indicate a bad cable or interface.

NetFlow: Tools to gather statistics about type of network traffic(UDP, TCP, etc.).

SLA: 
- Minimum terms for services provided.
- Uptime, response time agreement.

RAID: Redundant Array of Independent Disks.

UPS: Uninterruptible Power Supply.

High Availability: Always on, always available.
- You can have redundancy, but if those redundant systems are not up when the fault happens you won't have high availability.

RBAC(Role-Based Access Control): Permission based on role in the organization.

Zero trust: Inside an organization network no user is trusted, every user has to authenticate itself before getting access to organizational resources.

LDAP(Lightweight Directory Access Protocol): Protocol for reading and writing directories over an IP network.

Kerberos: Network auth protocol, authenticate once.

VLAN hopping: Moves from one VLAN to another.
- Switch spoofing: Takes advantage of a poorly configured trunk port and tricks other switches into thinking the attacker device is a switch trying to form a trunk connection.
- Double tagging: Something about packets VLAN tags.

Rogue DHCP server: IP addresses assign by a non-authorized server.
- Disable rogue DHCP communication:
	- Enable DHCP snooping on your switch.
	- Authorize DHCP servers in AD.

Rogue Access Point:
- Periodic surveys: With a third party tool(WiFi Pineapple) walk and scan for AP's.
- 802.1X(Network Access Control): You must authenticate, regardless of connection type.

Port security: Prevent unauthorized users from connecting to a switch.

Dynamic ARP Inspection(DAI): Use DHCP snooping to make decisions if an ARP request is legit or not, if it's not the request gets discarded.

DHCP snooping: Gives switch ability to track and manage IP's of devices in the network. Like a DHCP firewall.

Change default VLAN: Don't allow users in the default VLAN because this VLAN typically handles management traffic.

Wireless isolation: A device connected to a wireless network cannot communicate with another device in the same network.

WPA2/3:
- Personal: Uses a pre-shared key, every user shares the same key.
- Enterprise: Users are authenticated individually with an authentication server(RADIUS).

VPN: Encrypt data traversing a public network.
- Concentrator: Encryption/decryption access device.
	
Virtual Desktop Infrastructure(VDI): Virtual desktop in the cloud.

NetFlow: Probe and collector used to gather traffic statistics.

route/netstat -r: commands to get routing table.

tcpdump: Capture packets from the command line.

RSSI(Received Signal Strength Indication): Use to measure the strength of a radio signal.
- dBm(Decibel-milliwatts): The number of decibels per one milliwatt, the closer to zero the better:
	- -50dBm: Excellent
	- -70dBm: Good
	- -80dBm: Low
