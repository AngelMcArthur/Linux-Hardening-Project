# Linux-Hardening
<b>Objective</b> - Hardening Ubuntu Linux

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h1>Ubuntu Hardening</h1>

<h2>Update and Upgrade</h2>

- <b>1. Open a terminal and run the following commands:</b>
  - `sudo apt update && sudo apt upgrade -y`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Install Unattended-Upgrades</h2>

- <b>1. Install Unattended-Upgrades to automatically install security updates</b>
  - `sudo apt install unattended-upgrades`
  - `sudo dpkg-reconfigure -plow unattended-upgrades`
- ![image](https://github.com/AngelMcArthur/Linux-Hardening-Project/assets/55830075/a692a7ed-2fc1-4759-aa95-19f99743bf8a)

- <b>2. Press [Enter] for "Yes"</b>

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Remove Bloatware/Unnecessary Services</h2>

<h3>Remove Bloatware (choosing default installation when setting up makes this simpler)</h3>

- <b>1. List all packages</b>
  - `apt list --installed`
		
- <b>2. Remove packages</b>
- `sudo apt purge (place package names here separated by a space)`

<!-------------------------------------- SMALL BREAK -------------------------------------->

<h2>Disable Unnecessary Services</h2>

- <b>1. Check Running Services</b>
  - `sudo service --status-all`
		
- <b>2. Disable Services</b>
  - `sudo systemctl disable <service_name>`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Configure Firewall (UFW)</h2>

- <i>(Note) UFW come preinstalled on most Linux distros.</i>
	
- <b>1. Install and enable the Uncomplicated Firewall (UFW):</b>
  - `sudo apt install ufw`
  - `sudo ufw enable`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Secure SSH</h2>

- <i>(Note) If SSH is not needed, consider disabling it. If needed:</i>
	
- <b>1. Type in terminal:</b>
  - `sudo nano /etc/ssh/sshd_config`
		
- <b>2. Scroll down to PermitRootLogin yes and switch to:</b>
  - `PermitRootLogin no`
			
- <b>3. Save and quit out of nano</b>
  - a) Save - Ctrl + O
  - b) Confirm - Enter
  - c) Exit - Ctrl + X
			
- <b>4. Restart for changes to take effect</b>
  - `sudo service ssh restart`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Set Up Fail2Ban</h2>
	
- <b>1. Install and configure Fail2Ban to protect against brute-force attacks:</b>
  - `sudo apt install fail2ban`
			
- <b>2. Check if it is running</b>
- `systemctl status fail2ban.service`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Set up AppArmor</h2>
	
- <b>1. Install AppArmor:</b>
- <i>(Note) AppArmor enhances system security by confining programs to a limited set of resources. It is usually already installed on most distros.</i>
  - `sudo apt install apparmor apparmor-utils`
			
- <b>2. Check if running:</b>
  - `sudo apparmor_status | more`

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h2>Install Lynis and Perform Audit</h2>

- <b>1. Install Lynis security audits:</b>
  - `sudo apt install lynis`
			
- <b>2. Perform Scan</b>
  - `sudo lynis audit system`
			
- <b>3. Check log in "/var/log/lynis.log" or read the report that is put out in a readable format after the scan is done.</b>
  - `sudo cat /var/log/lynis.log`
			
- <b>4. Remedy issues</b>

<!---------------------------------------------------------------------- SECTION BREAK ---------------------------------------------------------------------->

<h1>Pentesting</h1>

<h2>1. General Vulnerability Scanners:</h2>

- Tool: OpenVAS (also consider sysechk and OpenSCAP)
  - Description: OpenVAS is an open-source vulnerability scanner that performs comprehensive vulnerability assessments.
  - Installation: Install on Ubuntu in Step 5 for Docker

<!-------------------------------------- SMALL BREAK -------------------------------------->

<h2>2. Network Vulnerabilities:</h2>

- Tool: Nmap
  - Description: Nmap is a powerful network scanning tool that can discover open ports, running services, and potential vulnerabilities.
  - Installation: Install on Ubuntu using
	-	`sudo apt install nmap`
		
- Run a few commands:
  - Scan a single target
  - `nmap [target]`
		
- Scan an entire subnet (Scan using CIDR notation)
  - `nmap [IP address/cdir]`
		
- Perform an aggressive scan
  - `nmap -A [target]`
		
- And more commands here https://www.stationx.net/nmap-cheat-sheet/ or https://www.geeksforgeeks.org/nmap-cheat-sheet/

<!-------------------------------------- SMALL BREAK -------------------------------------->


