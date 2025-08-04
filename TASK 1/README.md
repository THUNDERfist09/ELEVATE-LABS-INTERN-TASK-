1. Identify Your Local Network Range
Begin by identifying your system's local IP address and subnet to determine the scope of your scan.

Commands:
Linux: ip a

Windows: ipconfig

From the output, identify your IP address (e.g., 192.168.1.10) and subnet mask (e.g., 255.255.255.0 or /24), indicating your local network range (e.g., 192.168.1.0/24).

2. Discover Live Hosts
Scanning every device within the subnet enables a comprehensive assessment.

Ping Sweep (ICMP):

nmap -sn 192.168.1.0/24
Identifies active hosts by sending ping requests.

ARP Scan (for local networks):

sudo arp-scan -l
More effective in LAN environments where ICMP may be blocked.

3. Scan for Open Ports
Once active hosts are identified, scan for open TCP ports to discover exposed services.

TCP SYN Scan (Stealth Scan):

sudo nmap -sS 192.168.1.10
Performs a half-open scan to identify open ports without fully establishing a TCP connection.

Scan an Entire Subnet:

sudo nmap -sS 192.168.1.0/24
Efficiently discovers exposed ports across all reachable hosts.

Advanced Scan with Service and OS Detection:

sudo nmap -sS -sV -O 192.168.1.10
-sV: Detects service versions.

-O: Attempts OS fingerprinting.