# VoIP Home Lab Server

Senior capstone project at Georgia Southern University focused on building, configuring, and troubleshooting a Voice over IP (VoIP) lab to practice and visualize Session Initiation Protocol (SIP) call flows and network switching[cite: 1, 2].

## Overview & Architecture
I built a local VoIP lab using **Ubuntu Server** running **Asterisk** as the PBX server, paired with **Zoiper** SIP softphones on iOS and iPadOS devices and enterprise network switches[cite: 1, 2, 12, 13].

* **PBX & SIP Endpoints:** Installed Ubuntu Server and Asterisk, configured endpoint accounts in `pjsip.conf`, and set up dialplans and call routing rules in `extensions.conf` (including extension-to-extension calling, Echo testing, and Music on Hold)[cite: 2, 8].
* **IP Addressing & DHCP:** Started with static IP addressing on Zoiper endpoints, then deployed **Kea DHCP** (`kea-dhcp`) on Ubuntu Server to dynamically assign IP addresses across the lab.
* **Switching & VLANs:** Used console access via PuTTY to inspect/reset switch ports, configure access ports and VLANs, and verify active traffic[cite: 2, 3, 7].

## Hardware & Software Used
* **Server OS & PBX:** Ubuntu Server, Asterisk PBX[cite: 2]
* **DHCP:** Kea DHCP (`kea-dhcp`)
* **Endpoints:** Zoiper SIP client (iPhone and iPad)[cite: 2, 12, 13], Cisco IP Phone 7965 (PoE)[cite: 2, 11]
* **Network Switches:**
  * Cisco Catalyst 1000 Series (10-port)[cite: 2, 3]
  * HP ProCurve 48-port PoE switch (defunct internal PoE power supply)[cite: 2, 6]
  * Cisco Catalyst 3650 Series (48-port PoE)[cite: 2, 9]

## Lab Troubleshooting & Lessons Learned
* **Switch Progression & PoE Power Fault:** Started with a Cisco Catalyst 1000 switch before introducing a Power over Ethernet (PoE) desk phone[cite: 2, 3]. Swapped to an HP ProCurve 48-port PoE switch, tested an alternate wall outlet, and checked PoE power status via CLI—confirming an internal power fault preventing port power delivery[cite: 2, 6]. Swapped to a Cisco Catalyst 3650 PoE switch for reliable operation through the rest of the lab[cite: 2, 9].
* **Cisco 7965 Firmware & TFTP/DHCP Options:** Attempted to migrate a Cisco IP Phone 7965 from SCCP to SIP firmware using a TFTP server, SIP firmware files, and a factory reset sequence, but the unit remained locked to SCCP[cite: 2, 11]. Also explored how DHCP options can advertise a TFTP server automatically during endpoint provisioning.
* **Dialplan File Routing:** Resolved an early configuration mismatch where extension rules were initially placed in the wrong file before properly configuring `extensions.conf` and verifying live SIP/RTP call behavior[cite: 2, 4, 8].

## Documentation & Demos
* **Final Project Report:** Included in this repository (`Final Report_BranHall.pdf`)[cite: 2].
* **Screenshots & Recordings:** Add links or folders here for selected terminal captures, hardware photos, and call test recordings (Zoiper-to-Zoiper call, Music on Hold, and Echo test)[cite: 2, 4, 13].
