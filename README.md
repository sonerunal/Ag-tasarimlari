# Enterprise-Networking
## Vlan Database

| Vlan Number  | Vlan Name | Network Address | Virtual Ip | CSW1 Address | CSW2 Address 
| ------------- | ------------- | ------------- | -------------| -------------| -------------
| 10  | Management  | 10.0.1.0/24 | 10.0.1.1 | 10.0.1.2 | 10.0.1.3 
| 20  | Operations  | 10.0.2.0/24 | 10.0.2.1 | 10.0.2.2 | 10.0.2.3
| 30  | Board Of Directors  | 10.0.3.0/24 | 10.0.3.1 | 10.0.3.2 | 10.0.3.3  
| 40  | IT  | 10.0.4.0/24 | 10.0.4.1 | 10.0.4.2 | 10.0.4.3 
| 50  | QA  | 10.0.5.0/24 | 10.0.5.1 | 10.0.5.2 | 10.0.5.3 
| 60  | Servers  | 10.0.6.0/24 | 10.0.6.1 | 10.0.6.2 | 10.0.6.3 
| 70 | Voice  | 10.0.8.0/24 | 10.0.8.1 | 10.0.8.2 | 10.0.8.3
| 80 | Wi-Fi Corporate | 10.0.9.0/24 | 10.0.9.1 | 10.0.9.2 | 10.0.9.3
| 90| Wi-Fi Guest | 10.0.10.0/24 | 10.0.10.1 | 10.0.10.2 | 10.0.10.3

## STP Hsrp Redundancy 
* Operations(VLAN-20) And QA (VLAN-50) And Servers(VLAN-60) And Wi-Fi Corporate(VLAN-80) --> CSW1 Root Primary, CSW2 Root Secondary
* IT(VLAN-40) And Board Of Directors(VLAN-30) And Voice(VLAN-70) And Wifi Guest(VLAN-90)--> CSW1 Root Secondary, CSW2 Root Primary 

## Layer 3 Links 
* CSW1 - Firewall 10.1.0.0/30
* CSW2 - Firewall 10.2.0.0/30
* Dmz - Firewall 10.3.0.0/30
* Firewall - ISP1 DHCP
* Firewall - ISP2 DHCP

## DHCP Pool
*
