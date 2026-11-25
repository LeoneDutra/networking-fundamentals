# Networking, Linux & Windows Fundamentals

Notes, cheatsheets and packet/log analysis exercises covering the fundamentals every SOC analyst needs: TCP/IP, Linux, Windows event logging and Active Directory.

## Topics
- TCP/IP fundamentals, three-way handshake, common ports
- DNS, DHCP, ARP
- Routing and switching basics, subnetting, VLANs, NAT
- Firewall rules and network segmentation
- Packet capture and protocol analysis with Wireshark and tcpdump
- Linux administration and log analysis
- Windows event logging, Sysmon and Active Directory

## Exercises

| # | Exercise | Skills |
| --- | --- | --- |
| 01 | [Kettle & Cipher Brewing — "The Flowmeter Driver"](pcap-analysis/01-brewery-incident/) | Wireshark basics, port scan, SSH brute force, HTTP file carving, C2 beaconing |

## Roadmap

- [ ] Ports & protocols cheatsheet with 'what to look for in an attack'
- [ ] 3+ PCAP analyses with Wireshark screenshots and conclusions
- [ ] Windows Event ID cheatsheet with sample logs
- [ ] Bash script that summarizes `auth.log` (top failed-login IPs)

## Repository structure

```
cheatsheets/
topologies/      # EVE-NG / GNS3 lab topologies
configs/         # device and firewall configs used in the labs
lab-guides/      # step-by-step lab guides
pcap-analysis/
linux/
windows-ad/
scripts/
```

## Notes

Topologies can be used in EVE-NG, GNS3 or similar platforms. This repo replaces my earlier `network-fundamentals-lab`.

## Skills demonstrated

TCP/IP · DNS · TLS · Wireshark · tcpdump · Bash · Sysmon · Windows Event Logs · Active Directory · Kerberos

## Part of my cybersecurity portfolio

Career changer (head brewer → SOC / Cloud & AI Security), based in Calgary, AB. See all projects on my [GitHub profile](https://github.com/LeoneDutra).
