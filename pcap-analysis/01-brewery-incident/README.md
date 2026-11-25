# PCAP 01 — Bow River Brewing: "The Flowmeter Driver"

**Level:** beginner · **Tools:** Wireshark (or tshark) · **Time:** 2–3 h · **Capture:** [`bow-river-brewing.pcap`](bow-river-brewing.pcap) (745 packets, ~14 min)

> **Synthetic training data.** I generated this capture for practice. It uses private and documentation-only addresses (RFC 1918 / RFC 5737) and the reserved `.example` domain. The "malware" is a harmless text file with an `MZ` header. No real systems or organizations are involved.

## Scenario

Bow River Brewing is a craft brewery in Calgary. Its network is `10.10.20.0/24`:

| Host | IP |
| --- | --- |
| Gateway / DNS | 10.10.20.1 |
| Mail server | 10.10.20.5 |
| Intranet / file server | 10.10.20.10 |
| Office workstations | 10.10.20.11–50 |

On **2026-11-20** the brewery's IT contractor received an alert about "unusual outbound traffic". You are the SOC analyst. The firewall captured the traffic below. Find out what happened and write an incident summary.

## Questions

### Part A — Get oriented
1. What are the date/time (UTC) of the first and last packets, and the capture duration?
2. Which protocols appear in the capture? (Hint: *Statistics → Protocol Hierarchy*)
3. Which IP addresses talk the most? Which ones are **external**? (Hint: *Statistics → Conversations*)

### Part B — The internet-facing server
4. An external IP probes `10.10.20.10`. What is the IP, what kind of activity is it, and which TCP ports are **open**?
5. Right after that, the same IP targets one service repeatedly. Which service, how many connection attempts, and what SSH client software does the attacker report?
6. Based only on the traffic, can you tell if the attacker logged in successfully? Why or why not?

### Part C — The workstation
7. What is the **hostname** and **MAC address** of `10.10.20.15`? (Hint: DHCP)
8. Which suspicious domain does the workstation resolve, and to which IP?
9. What file is downloaded? Give the full URL, the file type it really is, its size and its **SHA256** hash. (Hint: *File → Export Objects → HTTP*, then `shasum -a 256 <file>`)
10. After the download, the workstation starts a repeating pattern. Describe it: method, URI, interval, User-Agent and number of requests. Why is that User-Agent suspicious?
11. The `id` parameter is encoded. Decode it. What does it reveal?

### Part D — Report
12. Build an **IOC table** (IPs, domain, URL, hash, User-Agent).
13. Map what you saw to **MITRE ATT&CK** techniques (at least 4).
14. Write a 5-line **executive summary** and 3 containment recommendations.

Write your answers in [`WRITEUP.md`](../templates/pcap-writeup.md) format (copy the template into this folder).

## Useful Wireshark display filters

```text
dhcp
dns
tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.flags.syn == 1 && tcp.flags.ack == 1
tcp.port == 22
http.request
http.request.method == "POST"
ip.addr == 203.0.113.66
```
