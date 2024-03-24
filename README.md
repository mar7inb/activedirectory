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


Installed DHCP server on DC which will allow our windows 10 clients to get an IP address that will let them browse the internet:


![dhcp](https://github.com/mar7inb/activedirectory/assets/90795866/1df08a99-f1be-4a4b-989e-fbc3071a3982)


Added 1k + users using Powershell ISE 


script explanation:


The password_for_users variable will give the users "password1" as a temporary password. 


The user_first_last_list variable will grab the users from . \names.txt and put it into an array. 


Then it will convert it into a string and lastly loop through the foreach until all users from the .\names.txt have been created. 


![powershell-users](https://github.com/mar7inb/activedirectory/assets/90795866/3f4607a1-4ef1-4886-93fb-372a11239ad4)



Opened CLIENT1 VM and configured a user: 


![userconfig](https://github.com/mar7inb/activedirectory/assets/90795866/fb7c841d-330e-444e-b943-ad3c477565b7)


We now have a lease from the client computer. When we created this client computer and joined it to the network it reached out to the DHCP server automatically and requested an address, the DHCP server then gave it an address and now we have this lease:


![dhcp2](https://github.com/mar7inb/activedirectory/assets/90795866/15e6f8e2-c3c9-41c6-906c-fa16fda38bbe)


## Conclusion


Client connects to the Domain Controller, the DC is NATING it/properly forwarding out to the internet and then it comes back with a reply. 


A more simple approach to what Active Directory is, it's an organized digital address book for a company, school, and/or organization. It keeps track of everyone who works or studies there, what they can do within the computer network and where they can go (sites they can visit and can't visit). It also helps by making sure only the right people have access to the right things (this is called authorization or access control.) on the system (files, printers, programs) while keeping unauthorized users out. We can think of active directory like a "digital bouncer". 


From a cybersecurity perspective, consider a malicious actor bypassing the "digital bouncer". Once inside, this actor could potentially access the organizations assets. 







































