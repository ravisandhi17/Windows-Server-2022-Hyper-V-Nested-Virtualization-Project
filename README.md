# Windows Server 2022 Hyper-V Nested Virtualization Lab

## Project Overview

This project demonstrates a fully functional enterprise-style Active Directory and Hyper-V environment built on a Dell PowerEdge R720 server running Windows Server 2022. The lab includes Active Directory Domain Services (AD DS), DNS, Hyper-V virtualization, nested virtualization, and domain-joined Windows 11 clients.

The objective of this project was to simulate a real-world IT infrastructure environment commonly used by system administrators, desktop support technicians, and infrastructure support teams.

---

## Lab Architecture
![IPCONFIG](screenshots/DC1/architecture.png)


---

## Technologies Used

* Dell PowerEdge R720
* Windows Server 2022
* Hyper-V
* Nested Virtualization
* Active Directory Domain Services (AD DS)
* DNS Server
* Windows 11
* PowerShell
* Remote Desktop Services

---

## Active Directory Configuration

### Domain Information

| Setting           | Value           |
| ----------------- | --------------- |
| Domain Name       | ravikumar.local |
| Domain Controller | DC1             |
| DNS Server        | 192.168.2.194   |

### Organizational Units

* HR_DELL
* IT_DELL
* SALES_DELL

### Domain-Joined Computers

* DC1
* HYPER-V-PC (NestedHostVM)
* DESKTOP-V8S8OM4 (Win11-Lab)

![IPCONFIG](screenshots/DC1/10-DC1-Active-Directory-Computers.png)


---

## Hyper-V Configuration

![IPCONFIG](screenshots/NestedHostVM/09-NestedHostVM-HyperV-Manager.png)

### DC1 Hyper-V Host

| Component      | Configuration  |
| -------------- | -------------- |
| Hyper-V Switch | ExternalSwitch |
| VM             | NestedHostVM   |
| VM State       | Running        |

![IPCONFIG](screenshots/DC1/Hyper-V-External-Virtual-Switch-Configuration.png)

![IPCONFIG](screenshots/DC1/Hyper-V-Virtual-Machine-Status.png)

![IPCONFIG](screenshots/NestedHostVM/Nested-Hyper-V-Virtual-Machine-Running-Inside-NestedHostVM.png)


### Nested Hyper-V Host

| Component       | Configuration |
| --------------- | ------------- |
| Hyper-V Enabled | Yes           |
| Nested VM       | Win11-Lab     |
| Virtual Switch  | LabSwitch     |

![IPCONFIG](screenshots/NestedHostVM/09-NestedHostVM-LabSwitch-Verification.png)

---

## Networking Configuration

### DC1

| Setting    | Value         |
| ---------- | ------------- |
| IP Address | 192.168.2.194 |
| DNS Server | 192.168.2.194 |
| Gateway    | 192.168.2.1   |

![IPCONFIG](screenshots/DC1/04-DC1-IPConfig-All.png)


### NestedHostVM

| Setting      | Value         |
| ------------ | ------------- |
| IP Address   | 192.168.2.196 |
| DNS Server   | 192.168.2.194 |
| LabSwitch IP | 192.168.2.198 |

![IPCONFIG](screenshots/NestedHostVM/05-NestedHostVM-IPConfig-All.png)


### Win11-Lab

| Setting    | Value           |
| ---------- | --------------- |
| IP Address | 192.168.2.200   |
| DNS Server | 192.168.2.194   |
| Domain     | ravikumar.local |


![IPCONFIG](screenshots/Win11-Lab/06-Win11-Lab-IPConfig-All.png)

---

## Validation Tests Performed

### DNS Resolution


nslookup ravikumar.local

![IPCONFIG](screenshots/Win11-Lab/07-Win11-Lab-NSLookup-Domain.png)



### Domain Membership Verification


systeminfo | findstr /B /C:"Domain"

![IPCONFIG](screenshots/Win11-Lab/08-Win11-Lab-Domain-Membership.png)



### Connectivity Testing

* DC1 ↔ NestedHostVM
* NestedHostVM ↔ Win11-Lab
* Win11-Lab ↔ DC1


![IPCONFIG](screenshots/Win11-Lab/ping94-from-win11-lab.png)

![IPCONFIG](screenshots/NestedHostVM/ping96-98-from-dc1.png)

---





## Skills Demonstrated

* Windows Server Administration
* Active Directory Management
* DNS Configuration and Troubleshooting
* Hyper-V Virtualization
* Nested Virtualization
* PowerShell Administration
* Network Configuration
* Domain Join Operations
* Enterprise Infrastructure Deployment
* IT Support and System Administration

---

## Author

**Ravi Kumar**

