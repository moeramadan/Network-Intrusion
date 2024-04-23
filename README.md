# WiFi Network Penetration Testing: Intrusion, Reconnaissance, and Traffic Monitoring

## Project Overview
This project demonstrates a network attack utilizing my home WiFi network. The intruder will locate the network, gain access, scan local devices, and commence tapping the outbound traffic of a target device through ARP Poisoning.

## Setup
For this project, Parrot OS will be utilized along with a network adapter and the following tools:
- `airodump-ng`
- `aireplay-ng`
- `hashcat`
- `nmap`
- `ettercap`
- `wireshark`

## Network Reconnaissance
Begin by setting the adapter in monitor mode and employ `airodump-ng` to monitor networks within range. Target a network, acquire their BSSID, and determine the operating channel. Utilize `airodump` to associate clients with the access point, retrieve client MAC addresses, and commence collecting network traffic in a dumpfile.

![Screenshot: Network Reconnaissance 1](https://github.com/moeramadan/Network-Intrusion/assets/155490852/aacec2a5-df73-4e82-8a7b-43cdbd30b33a)
![Screenshot: Network Reconnaissance 2](https://i.ibb.co/t3QBV6w/chrome-AWO7o-Ah-Qsx.png)
![Screenshot: Network Reconnaissance 3](https://i.ibb.co/cbZ4Bt4/chrome-e-QFbyr-Qwv-O.png)

## De-authentication Attack
Employ `aireplay-ng` to target a client and transmit deauthentication packets to disassociate them from the AP, effectively removing them from the network.

![Screenshot: De-authentication Attack 1](https://i.ibb.co/cCsC9Xz/chrome-a-CXl-Wp-Hbtx.png)
![image](https://github.com/moeramadan/Network-Intrusion/assets/155490852/49ad31f1-fafb-4f14-9413-d2df6c164a02)


## EAPOL Handshake Capture
As the device reconnects to the network, `airodump` captures the WPA handshake between the client and the AP. Verify all parts of the EAPOL message using Wireshark.

![Screenshot: EAPOL Handshake Capture 1](https://i.ibb.co/r7PxGSB/chrome-v-OD8z-Y9-IPg.png)
![Screenshot: EAPOL Handshake Capture 2](https://i.ibb.co/cvmxnFf/chrome-z-Qh-Nf-JBQGo.png)

## Hashcat Password Crack
Convert the captured file for use with `hashcat` and execute a dictionary attack using the 'rockyou' wordlist along with a rule list 'best64'. Weak or previously breached passwords will be cracked, and their associated hash will be revealed.

![Screenshot: Hashcat Password Crack 1](https://github.com/moeramadan/Network-Intrusion/assets/155490852/a5b003fb-d3ea-4944-9fc5-b95177c46991)
![Screenshot: Hashcat Password Crack 2](https://i.ibb.co/k8nmGkt/chrome-V4rl-OBW2f-Q.png)

## Further Reconnaissance
Access the network using the cracked password, retrieve the local IP using `ifconfig`, and conduct a network scan with `nmap`. Utilize `nmap` to identify vulnerabilities, scan hosts, and select a suitable target.

![Screenshot: Further Reconnaissance](https://i.ibb.co/HNQ7Fpc/chrome-a-XPYgx-Uqx-N.png)

## ARP Poisoning and Man-in-the-Middle
Utilize `ettercap` to orchestrate a man-in-the-middle attack, positioning oneself between the router and the client, clandestinely forwarding and capturing traffic.

![Screenshot: ARP Poisoning and Man-in-the-Middle](https://i.ibb.co/pWxZ3Pb/chrome-Odws-ZNo-BPE.png)

## Packet Analysis
Utilize Wireshark for comprehensive packet capture and analysis. Online tools can be employed to analyze `.pcap` files for ease of use.

![Screenshot: Packet Analysis 1](https://i.ibb.co/cY6q2Xv/chrome-48-Re-JHrb-W2.png)
![Screenshot: Packet Analysis 2](https://i.ibb.co/ypPWbL2/chrome-EGx-THq2d-P5.png)
![Screenshot: Packet Analysis 3](https://github.com/moeramadan/Network-Intrusion/assets/155490852/9c2adc58-fa42-4764-bf0e-ef0e2b302b40)
