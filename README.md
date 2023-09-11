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

## Simplified process on how to build 

Note: This is a very simplified process, make sure to research if you don't know how to do any of the steps. 

1. Download all tools (oracle vm, server 2019 iso, windows 10 iso)
   
   links:
   
   https://www.virtualbox.org/wiki/Downloads - download extension pack as well
   
   https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
   
   https://www.microsoft.com/en-us/software-download/windows10 - you will need to convert this to ISO so please google how to do that, very simple process.

   IMPORTANT: Make sure to save all of these files to your desktop. 

2. Creat a VM called DC with Oracle Virtual Box

   To be Continued...


## Powershell script used to add users 


$PASSWORD_FOR_USERS   = "Password1"
$USER_FIRST_LAST_LIST = Get-Content .\names.txt


$password = ConvertTo-SecureString $PASSWORD_FOR_USERS -AsPlainText -Force
New-ADOrganizationalUnit -Name _USERS -ProtectedFromAccidentalDeletion $false


foreach ($n in $USER_FIRST_LAST_LIST) {
    $first = $n.Split(" ")[0].ToLower()
    $last = $n.Split(" ")[1].ToLower()
    $username = "$($first.Substring(0,1))$($last)".ToLower()
    Write-Host "Creating user: $($username)" -BackgroundColor Black -ForegroundColor Cyan
    
    
    New-AdUser -AccountPassword $password `
               -GivenName $first `
               -Surname $last `
               -DisplayName $username `
               -Name $username `
               -EmployeeID $username `
               -PasswordNeverExpires $true `
               -Path "ou=_USERS,$(([ADSI]`"").distinguishedName)" `
               -Enabled $true
}


Script Explanation: 



