# activedirectory
# Home lab running Active Directory using Oracle VirtualBox and adding users with Powershell
![Active Directory ](https://github.com/mar7inb/activedirectory/assets/90795866/c1d0121c-d9ea-4072-8ad4-81fa4ab68058)

## Intro

In this project I built an Active Directory Lab using VirtualBox. I then used a Powershell script to add over 1k users. 

## Tools used in this project

Oracle VirtualBox

Server 2019 ISO

Windows 10 ISO 

## Glossary

NIC: Network Interface Card. This is a hardware component that allows a computer/device to connect to a network such as a LAN (Local Area Network) or internet. 

DC: Domain Control. This is responsible for user authentication, access control, and management of network resources. 

DHCP: Dynamic Host Configuration Protocol. This is used to automatically assign IP addresses and simplifies network administration by eliminating the need for manual IP address assignments, allowing devices to obtain their network settings dynamically when they connect to the network. This protocol is used in home and business networks to efficiently connect phones, computers and printers. 

RAS: Remote Access Server. This enables secure access to resources within a private network from external location/s.

NAT: Network Address Translation. Technique used to allow multiple devices on a local network to share a public IP address in order to connect to the internet. This also helps by hiding local network structures from external sources. 

FQDN: Fully Qualified Domain Name. This identifies a location on the internet or local network. In this project I used "mydomain.com" to keep it simple.

## Project: 


Created both virtual machines and added their respective ISO:


![oraclevm1](https://github.com/mar7inb/activedirectory/assets/90795866/511e7259-6498-44e5-a745-b0e7714aeaf8)


![oraclevm2](https://github.com/mar7inb/activedirectory/assets/90795866/8e4b3967-4094-4df7-a9b1-6a67700ce485)


Identified internal network and set up IP addressing:

![ipaddressing1](https://github.com/mar7inb/activedirectory/assets/90795866/286a2883-c7bc-4ecb-9165-8377b25c170b)


![ipaddressing2](https://github.com/mar7inb/activedirectory/assets/90795866/6eeb2af9-5841-4443-9c22-da95d4dcb9ab)


Installed Active Directory Domain Services

![ad1](https://github.com/mar7inb/activedirectory/assets/90795866/648c4bfc-a091-4bbb-8750-9b22ddc2b0f2)


![ad2](https://github.com/mar7inb/activedirectory/assets/90795866/84bc6c17-cea8-4be6-8fca-c1928318f8e7)


Created a Domain Admin


![domainadmin](https://github.com/mar7inb/activedirectory/assets/90795866/3554cb0a-d14d-4cb5-b076-99a872aa1236)


Created Routing and Remote Access


![routing](https://github.com/mar7inb/activedirectory/assets/90795866/f6e93365-9109-4117-91e5-38ac3b5c9a21)


Installed NAT which will allow internal clients to connect to the internet using one public IP address:


![nat](https://github.com/mar7inb/activedirectory/assets/90795866/91051481-bb65-4954-b006-b9c7b7668ce0)



























