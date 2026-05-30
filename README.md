# Windows Server 2022 Hyper-V Nested Virtualization Lab

## Project Overview

This project demonstrates a fully functional enterprise-style Active Directory and Hyper-V environment built on a Dell PowerEdge R720 server running Windows Server 2022. The lab includes Active Directory Domain Services (AD DS), DNS, Hyper-V virtualization, nested virtualization, and domain-joined Windows 11 clients.

The objective of this project was to simulate a real-world IT infrastructure environment commonly used by system administrators, desktop support technicians, and infrastructure support teams.

---

## Lab Architecture

```text
Dell PowerEdge R720
│
├── DC1 (Windows Server 2022)
│   ├── Active Directory Domain Services
│   ├── DNS Server
│   ├── Hyper-V Host
│   └── IP Address: 192.168.2.194
│
└── NestedHostVM (Windows 11)
    ├── Hyper-V Enabled
    ├── Domain Joined
    ├── IP Address: 192.168.2.196
    │
    └── Win11-Lab (Windows 11)
        ├── Nested Virtual Machine
        ├── Domain Joined
        ├── DNS Resolution
        └── IP Address: 192.168.2.200
```

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

---

## Hyper-V Configuration

### DC1 Hyper-V Host

| Component      | Configuration  |
| -------------- | -------------- |
| Hyper-V Switch | ExternalSwitch |
| VM             | NestedHostVM   |
| VM State       | Running        |

### Nested Hyper-V Host

| Component       | Configuration |
| --------------- | ------------- |
| Hyper-V Enabled | Yes           |
| Nested VM       | Win11-Lab     |
| Virtual Switch  | LabSwitch     |

---

## Networking Configuration

### DC1

| Setting    | Value         |
| ---------- | ------------- |
| IP Address | 192.168.2.194 |
| DNS Server | 192.168.2.194 |
| Gateway    | 192.168.2.1   |

### NestedHostVM

| Setting      | Value         |
| ------------ | ------------- |
| IP Address   | 192.168.2.196 |
| DNS Server   | 192.168.2.194 |
| LabSwitch IP | 192.168.2.198 |

### Win11-Lab

| Setting    | Value           |
| ---------- | --------------- |
| IP Address | 192.168.2.200   |
| DNS Server | 192.168.2.194   |
| Domain     | ravikumar.local |

---

## Validation Tests Performed

### DNS Resolution

```cmd
nslookup ravikumar.local
```

Result:

```text
Name: ravikumar.local
Address: 192.168.2.194
```

### Domain Membership Verification

```cmd
systeminfo | findstr /B /C:"Domain"
```

Result:

```text
Domain: ravikumar.local
```

### Connectivity Testing

* DC1 ↔ NestedHostVM
* NestedHostVM ↔ Win11-Lab
* Win11-Lab ↔ DC1
* DNS Resolution Successful

---

## Screenshots

### Hyper-V Configuration

* 01-DC1-Get-VMSwitch.png
* 02-DC1-Get-VM.png
* 03-NestedHostVM-Get-VM.png

### Network Configuration

* 04-DC1-IPConfig-All.png
* 05-NestedHostVM-IPConfig-All.png
* 06-Win11-Lab-IPConfig-All.png

### Domain Services

* 07-Win11-Lab-NSLookup-Domain.png
* 08-Win11-Lab-Domain-Membership.png
* 09-NestedHostVM-HyperV-Manager.png
* 10A-DC1-Domain-Controllers-OU.png
* 10B-DC1-Domain-Joined-Computers.png

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

GitHub: https://github.com/ravisandhi17

LinkedIn: https://linkedin.com/in/ravi-kumar-724255411
