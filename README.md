# Setup Virtual Machines for the Introduction to Docker and Kubernetes Class

The following instructions are for `student1`. Repeat for each student in the class incrementing the number each time. For example, the second student would be `student2`. Please create an instance for the `instructor` as well.

## Setup Windows Server (Repeat for each Student)

- Create a Windows Server Instance with the following settings:
  - Name: `student1-windows-instance`
  - Region: `us-east4`
  - Zone: `us-east4-c`
  - Series: `E2`
  - Machine Type: `e2-standard-2 (2vCPU, 8 GB Memory)`
  - Operating system: `Windows Server`
  - Version: `Windows Server 2019 Data Center - with Desktop Experience`
  - Boot disk type: `Standard persistent disk`
  - Size: `100` GB

- Setup a Windows Password
  - Specify a username: `student1`
  - Copy the password and save it
  - Download the RDP File
  - Open an RDP Session with the RDP File

- Disable IE Enhanced Security Configuration
  - Open Server Manager
  - Click on Local Server on the sidebar menu
  - In the top box, second column, second row group, third setting down, `IE Enhanced Security Configuration`, click on `On`
  - Disable the enhanced security for the admin and normal users

- Open Internet Explorer, download and install Chrome: [https://www.google.com/chrome](https://www.google.com/chrome)

- Open Internet Explorer, download and install VS Code: [https://code.visualstudio.com](https://code.visualstudio.com)
  - Accept the defaults in the installation steps, for the "Select Additional Tasks" step, select all five options, complete the install


## Create Linux Instance (Repeat for each Student)

- Create a new Linux Instance with the following settings:
  - Name: `student1-linux-instance`
  - Region: `us-east4`
  - Zone: `us-east4-c`
  - Series: `E2`
  - Machine Type: `e2-standard-2 (2vCPU, 8 GB Memory)`
  - Operating system: `Ubuntu`
  - Version: `Ubuntu 20.04 LTS`
  - Boot disk type: `SSD persistent disk`
  - Size: `100` GB


- Setup Linux Login
  - Start a PowerShell Session.
  - Create an SSH certificate on the Windows Server

    - Note: Leave the password empty.

```powershell
```

  - Use the certificate to connect to the Linux server

```powershell
```

    - The user should be logged in and presented with the Linux server terminal prompt

- From the Linux terminal, run OS Updates

```bash
sudo apt update

sudo apt upgrade
```

## Student Information for their Virtual Machines (Repeat for each Student)

- Please provide a zip file for each student which contains the following:
 - The RDP file
 - Server Information File

- The server information file will need the following information:
 - Windows Server username
 - Windows Server password
 - Windows Server external IP address
 - Linux Server external IP address
 - Information needed to connect to the Windows Server VM through the web browser

- Note: Please provide the Window Server RDP file in case a student is using a personal machine and want to connect to the Windows Server without having to use the web browser.

## Firewall Rule for k8s Dashboard (Performed Once, See Note)

- Note: If all Windows Server and Linux servers are created within the same VPC network, then this rule only needs to be added once.

- Add a firewall rule to allow all TCP traffic to all IPs on port 10443, here are the settings:
  - Name: `k8s-dashboard`
  - Direction of Traffic: `Ingress`
  - Action on match: `Allow`
  - Targets: `All instances in the network`
  - Source filter: `IP ranges`
  - Source IP ranges: `0.0.0.0/0`
  - Protocols and ports
    - Specified protocols and ports:
      - `tcp`: `10443`

### IMPORTANT: Please email the instructor a Google Drive link (or another file sharing service) with all of the zip files the morning of the business day before the class starts (US federal holidays are not a business day), so the instructor can randomly try some of the student accounts to ensure a proper setup.