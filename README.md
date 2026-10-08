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
| WLC | Vlan 1 | 10.0.0.0/24 | 10.0.0.1 | 10.0.6.4

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
| 90 | Wi-Fi Guest | 10.0.9.0/24 | 10.0.9.1 | 10.0.9.2 | 10.0.9.3
| 1 | Ap-Management(CAPWAP) | 10.0.0.0/24 | 10.0.0.1 | 10.0.0.2 | 10.0.0.3

## Hsrp redundancy and Spanning tree root bridge
|  CSW1  | CSW2  
| ------------- | ------------- 
| Vlan 20 Active | Vlan 20 Standby 
| Vlan 30 Standby | Vlan 30 Active
| Vlan 40 Standby | Vlan 40 Active
| Vlan 50 Active | Vlan 50 Standby 
| Vlan 60 Active | Vlan 60 Standby 
| Vlan 70 Standby | Vlan 70 Active
| Vlan 80 Active | Vlan 80 Standby
| Vlan 90 Standby | Vlan 90 Active
| Vlan 1 Active | Vlan 1 Standby 

<img width="753" height="266" alt="image" src="https://github.com/user-attachments/assets/ba04d307-3cab-4ed2-af63-d8eb18c1a46d" />

## Layer 3 Links 
* CSW1 - R1 10.1.0.0/30
* CSW2 - R1 10.2.0.0/30
* R1 - ISP1 DHCP
* R1 - ISP2 DHCP
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
* Vlan 1 10.0.0.0/24 Exclude 10.0.0.1 - 10.0.0.10

## Access Switch 
* F0/4 --> Access point 
* F0/1 - 3 --> Ip Phones
* G0/1 - 2 --> CSW1 - CSW2
  
###  Show vlan and trunk ports at SWK-1
<img width="649" height="264" alt="image" src="https://github.com/user-attachments/assets/7c76265a-e96b-4dff-95d1-dcc47c3d0fe0" />
<img width="646" height="237" alt="image" src="https://github.com/user-attachments/assets/cbfd70f1-4f2c-42bb-926a-8c8da9a85151" />

### Between CSW1 and CSW2 layer 2 ether channel mode lcap active
<img width="754" height="360" alt="image" src="https://github.com/user-attachments/assets/feac154f-e33e-4716-a48b-c20f843e6fff" />

### Ospf command 
CSW1 --> Network 10.1.0.2 0.0.0.0 area 0
CSW2 --> Network 10.2.0.2 0.0.0.0 area 0

## R1(ASBR) Configuration 
### Default static routes 
ip route 0.0.0.0 0.0.0.0 203.0.113.1 (via isp1) 
ip route 0.0.0.0 0.0.0.0 203.0.112.1 5 (via isp2)
### Ospf Command
Network 10.2.0.1 0.0.0.0 area 0
Network 10.1.0.1 0.0.0.0 area 0 
Default information orginate
### Nat Command
int G6/0 - G7/0 --> ip nat inside 
int G8/0 - G9/0 --> ip nat outside 
access list 10 permit 10.0.0.0 0.0.0.255  
access list 11 permit 10.0.0.0 0.0.0.255  
ip nat inside source list 10 interface G8/0 overload 
ip nat inside source list 11 interface G9/0 overload

## Router ospf cost 
| Vlan |  CSW1 | CSW2 
| ------------- | -------------  | ------------- 
| 20 | 10 | 100
| 30 | 100 | 10
| 40 | 100 | 10
| 50 | 10 | 100
| 60 | 10 | 100
| 70 | 100 | 10
| 80 | 10 | 100
| 90 | 100 | 10
| 1 | 10 | 100

### CSW1 and CSW2 
passive-interface default 
no passive interface g0/1 (to R1 interface)

## Syslog and Ntp 
ntp server 10.0.6.5
logging host 10.0.6.5
logging on 
logging trap debugging 
service timestamps log datetime msec

## ACL
ip access-list extended 100 
permit dns 
permit ntp 
deny any to host 10.0.6.5(server)
permit ip any any 
