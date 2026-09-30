# Enterprise-Networking

## Access Credential 
* SSH Username & Password : admin & admin123 
* Enable Secret : ccna 
* Vty Lines : Login local

## Devices 
| Hostname | İnterface | Ip Address | Default Gateway | Dns Server
| ------------- | ------------- | ------------- | ------------- | -------------
| CSW1 | Vlan 10 | 10.0.1.2/24 | 10.1.0.1 | 10.0.6.4
| CSW2 | Vlan 10 | 10.0.1.3/24 | 10.2.0.1 | 10.0.6.4
| SWK-1 | Vlan 10 | 10.0.1.4/24 | 10.0.1.1 | 10.0.6.4 
| SWK-2 | Vlan 10 | 10.0.1.5/24 | 10.0.1.1 | 10.0.6.4 
| SWK-3 | Vlan 10 | 10.0.1.6/24 | 10.0.1.1 | 10.0.6.4  
| SERVERS | Vlan 10 | 10.0.1.7/24 | 10.0.1.1 | 10.0.6.4
| DMZ | Vlan 10 | 10.0.1.8/24 | 10.0.1.1 | 10.0.6.4


## Vlan Database
|  Vlan Number  | Vlan Name | Network Address | Virtual Ip | CSW1 Address | CSW2 Address 
| ------------- | ------------- | ------------- | -------------| -------------| -------------
| 10  | Management  | 10.0.1.0/24 | 10.0.1.1 | 10.0.1.2 | 10.0.1.3 
| 20  | Operations  | 10.0.2.0/24 | 10.0.2.1 | 10.0.2.2 | 10.0.2.3
| 30  | Board Of Directors  | 10.0.3.0/24 | 10.0.3.1 | 10.0.3.2 | 10.0.3.3  
| 40  | IT  | 10.0.4.0/24 | 10.0.4.1 | 10.0.4.2 | 10.0.4.3 
| 50  | QA  | 10.0.5.0/24 | 10.0.5.1 | 10.0.5.2 | 10.0.5.3 
| 60  | Servers  | 10.0.6.0/24 | 10.0.6.1 | 10.0.6.2 | 10.0.6.3 
| 70 | Voice  | 10.0.7.0/24 | 10.0.7.1 | 10.0.7.2 | 10.0.7.3
| 80 | Wi-Fi Corporate | 10.0.8.0/24 | 10.0.8.1 | 10.0.8.2 | 10.0.8.3
| 90| Wi-Fi Guest | 10.0.9.0/24 | 10.0.9.1 | 10.0.9.2 | 10.0.9.3
| 95| Ap-Management(CAPWAP) | 10.0.95.0/24 | 10.0.95.1 | 10.0.95.2 | 10.0.95.3

## Hsrp redundancy  
|  CSW1  | CSW2  
| ------------- | ------------- 
| Vlan 20 Active | Vlan 20 Standby 

* Operations(VLAN-20) And QA (VLAN-50) And Servers(VLAN-60) And Wi-Fi Corporate(VLAN-80), Ap-Management(Vlan-95)) --> CSW1 Root Primary, CSW2 Root Secondary
* IT(VLAN-40) And Board Of Directors(VLAN-30) And Voice(VLAN-70) And Wifi Guest(VLAN-90)--> CSW1 Root Secondary, CSW2 Root Primary 

<img width="753" height="266" alt="image" src="https://github.com/user-attachments/assets/ba04d307-3cab-4ed2-af63-d8eb18c1a46d" />

## Layer 3 Links 
* CSW1 - Firewall 10.1.0.0/30
* CSW2 - Firewall 10.2.0.0/30
* Dmz - Firewall 10.3.0.0/30
* Firewall - ISP1 DHCP
* Firewall - ISP2 DHCP
* DNS Server - 10.0.6.4 255.255.255.0
* Web Server - 10.3.0.2 255.255.255.252

### Routing: CSW1-CSW2-FW arasında OSPF Area 0
### CSW1 <-> CSW2: Port-Channel 1 (LACP, Trunk)

## DHCP Pool 
* Vlan 20 10.0.2.0/24 Exclude 10.0.2.1 - 10.0.2.10
* Vlan 30 10.0.3.0/24 Exclude 10.0.3.1 - 10.0.3.10
* Vlan 40 10.0.4.0/24 Exclude 10.0.4.1 - 10.0.4.10
* Vlan 50 10.0.5.0/24 Exclude 10.0.5.1 - 10.0.5.10
* Vlan 70 10.0.7.0/24 Exclude 10.0.7.1 - 10.0.7.10
* Vlan 80 10.0.8.0/24 Exclude 10.0.8.1 - 10.0.8.10
* Vlan 90 10.0.9.0/24 Exclude 10.0.9.1 - 10.0.9.10
* Vlan 95 10.0.95.0/24 Exclude 10.0.95.1 - 10.0.95.10

## Access Switch 
* F0/4 --> Access point 
* F0/1 - 3 --> Ip Phones
* G0/1 - 2 --> CSW1 - CSW2
  
###  Show vlan and trunk ports at SWK-1
<img width="649" height="264" alt="image" src="https://github.com/user-attachments/assets/7c76265a-e96b-4dff-95d1-dcc47c3d0fe0" />
<img width="646" height="237" alt="image" src="https://github.com/user-attachments/assets/cbfd70f1-4f2c-42bb-926a-8c8da9a85151" />

### Between CSW1 and CSW2 layer 2 ether channel mode lcap active
<img width="754" height="360" alt="image" src="https://github.com/user-attachments/assets/feac154f-e33e-4716-a48b-c20f843e6fff" />





