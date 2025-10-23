🧾 Description — Demonstrating ARP Spoofing and Detection

This lab demonstrates how Address Resolution Protocol (ARP) spoofing works, how an attacker can manipulate ARP tables to intercept network traffic, and how to detect and mitigate such attacks using Wireshark and other tools.

🧠 Objective

Understand and simulate an ARP spoofing attack within a controlled environment to visualize how attackers perform Man-in-the-Middle (MITM) operations and how defenders can identify and respond to them.

🧰 Tools Required

Kali Linux VM (attacker)

Windows or Linux VM (victim)

Wireshark (for detection and analysis)

arpspoof tool from the dsniff suite

⚙️ Lab Steps Summary

Enable IP forwarding on the attacker’s machine
Allows the attacker to forward traffic and maintain connectivity between victim and gateway.

echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward


Perform ARP Spoofing using arpspoof
Sends fake ARP replies to associate the attacker’s MAC with the gateway’s IP address.

sudo arpspoof -i eth0 -t [Victim_IP] [Gateway_IP]


Monitor ARP Tables
On the victim system (Windows/Linux), verify ARP table changes.

arp -a


Analyze with Wireshark

Capture traffic on the network interface.

Use ARP filter:

arp


Identify unsolicited ARP replies showing the attacker’s MAC claiming the gateway’s IP.

Detection and Mitigation

Use Wireshark, ARPwatch, or XArp to monitor MAC-IP bindings.

Implement Dynamic ARP Inspection (DAI) on managed switches.

Disable IP forwarding after the test:

echo 0 | sudo tee /proc/sys/net/ipv4/ip_forward

🔎 What You Learn

How ARP spoofing enables packet interception or redirection.

How to recognize an ARP poisoning attack by analyzing ARP responses.

The importance of secure network segmentation and ARP inspection.

⚠️ Important Note

This exercise must only be performed in a controlled lab environment.
Running ARP spoofing on a production or public network is illegal and unethical.
