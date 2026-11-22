# VoIP Home Lab Server

Senior capstone project at Georgia Southern University focused on building, configuring, and troubleshooting a Voice over IP (VoIP) lab to practice and visualize Session Initiation Protocol (SIP) call flows and network switching.

## Overview & Architecture
I built a local VoIP lab using **Ubuntu Server** running **Asterisk** as the PBX server, paired with **Zoiper** SIP softphones on iOS and iPadOS devices and enterprise network switches.

* **PBX & SIP Endpoints:** Installed Ubuntu Server and Asterisk, configured endpoint accounts in `pjsip.conf`, and set up dialplans and call routing rules in `extensions.conf` (including extension-to-extension calling, Echo testing, and Music on Hold).
* **IP Addressing & DHCP:** Started with static IP addressing on Zoiper endpoints, then deployed **Kea DHCP** (`kea-dhcp`) on Ubuntu Server to dynamically assign IP addresses across the lab.
* **Switching & VLANs:** Used console access via PuTTY to inspect/reset switch ports, configure access ports and VLANs, and verify active traffic.

## Hardware & Software Used
* **Server OS & PBX:** Ubuntu Server, Asterisk PBX
* **DHCP:** Kea DHCP (`kea-dhcp`)
* **Endpoints:** Zoiper SIP client (iPhone and iPad), Cisco IP Phone 7965 (PoE)
* **Network Switches:**
  * Cisco Catalyst 1000 Series (10-port)
  * HP ProCurve 48-port PoE switch (defunct internal PoE power supply)
  * Cisco Catalyst 3650 Series (48-port PoE)

## Lab Troubleshooting & Lessons Learned
* **Switch Progression & PoE Power Fault:** Started with a Cisco Catalyst 1000 switch before introducing a Power over Ethernet (PoE) desk phone. Swapped to an HP ProCurve 48-port PoE switch, tested an alternate wall outlet, and checked PoE power status via CLI—confirming an internal power fault preventing port power delivery. Swapped to a Cisco Catalyst 3650 PoE switch for reliable operation through the rest of the lab.
* **Cisco 7965 Firmware & TFTP/DHCP Options:** Attempted to migrate a Cisco IP Phone 7965 from SCCP to SIP firmware using a TFTP server, SIP firmware files, and a factory reset sequence, but the unit remained locked to SCCP. Also explored how DHCP options can advertise a TFTP server automatically during endpoint provisioning.
* **Dialplan File Routing:** Resolved an early configuration mismatch where extension rules were initially placed in the wrong file before properly configuring `extensions.conf` and verifying live SIP/RTP call behavior.

## Documentation & Photos
* **Final Project Report:** Included in this repository (`VoIPHomeLabServerFinalReport_BranHall.pdf`).
* **Photos:** Individual photos are located in the photos folder in the repository.

## Videos
* **Echo and MusicOnHold test being conducted** https://youtube.com/shorts/YHdhLg81khU?feature=share
* User-to-user test https://youtu.be/LFRE6CzIFaA
* User-to-user test pt2 https://youtube.com/shorts/ohHFGnaXg5s?feature=share
