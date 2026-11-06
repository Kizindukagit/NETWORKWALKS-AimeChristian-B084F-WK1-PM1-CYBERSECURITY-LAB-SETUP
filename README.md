# NETWORKWALKS-AimeChristian-B084F-WK1-PM1-CYBERSECURITY-LAB-SETUP
Cybersecurity Lab Setup – Week 1
![Uploading image.png…]()
Challenge 1: Network Configuration and Connectivity Troubleshooting

1. Network Setup

Configured three virtual machines in Oracle VirtualBox using the same NAT Network (10.0.0.0/24).

Virtual Machine

IP Address

Kali Linux

10.0.0.2

Android

10.0.0.9

Windows 11

10.0.0.11

2. Configuring Kali Linux

Assigned Kali Linux the static IP address:

sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up

Verified the configuration:

ip addr show

3. Identifying the Problem

During connectivity testing, Windows 11 could successfully ping Kali Linux, but Kali Linux could not successfully ping Windows 11.

Cause: Windows Defender Firewall was blocking incoming ICMP Echo Requests (ping).

4. Solution: Enable Ping Through Windows Firewall

Opened Windows PowerShell or Command Prompt as Administrator and executed:

netsh advfirewall firewall add rule name="Allow Ping (ICMPv4-In)" protocol=icmpv4:8,any dir=in action=allow

This command creates an inbound firewall rule allowing ICMPv4 Echo Requests (Type 8), enabling other devices on the network to ping Windows 11.

5. Connectivity Testing

From Kali Linux, executed:

ping 10.0.0.11

The ping test confirmed connectivity between Kali Linux and Windows 11.

6. Lessons Learned

Configuring static IP addresses in Linux, Windows, and Android.

Configuring NAT Networks in VirtualBox.

Using the ping command for connectivity testing.

Troubleshooting ICMP connectivity issues.

Managing Windows Defender Firewall rules using the command line.

Conclusion: Successfully resolved the network connectivity challenge by configuring IP addresses and allowing ICMP traffic through Windows Defender Firewall.
