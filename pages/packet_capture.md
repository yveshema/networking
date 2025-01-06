---
permalink: /packet-capture
---

# Packet Capture

Complete the following activities starting and stopping the packet capture as requested. Steps prefaced with "Issue command" are executed in the terminal.

<details>
    <summary>Capture 1</summary>
    
    1. Issue command:
       - Windows from Administrator Powershell: `Remove-NetNeighbor *`
       - Linux: `sudo ip neigh flush all`
       - MacOS: `sudo arp -a -d`
    2. Start Capture
    3. Issue command:
       - Windows from Administrator CMD: `ping -n 5 www.google.ca`
       - Windows from Administrator Powershell: `Test-Connection -Count 5 www.google.ca`
       - Linux: `ping -c 5 www.google.ca`
       - MacOS: `ping -c 5 www.google.ca`
       - Stop Capture
    4. Save as **Capture1.pcap**

</details>

<details>
    <summary>Capture 1</summary>
    
    1. Clear the cache from firefox / chrome / edge (`<ctrl><shift><delete>`)
    2. Start capture
    3. Using a web browser visit `http://www.undeadly.org`
    4. Stop Capture
    Save as **Capture2.pcap**

</details>

<details>
    <summary>Capture 3</summary>
    
    1. Start capture
    2. Issue command:
       - Windows from Administrator Powershell: `ipconfig /renew`
       - Linux: `sudo dhclient -r -pf /var/run/dhclient-em1.pid`
       - Stop capture
    3. Save as **Capture3.pcap**
   
</details>

<details>
    <summary>Analysis</summary>
    
    Reload each of the previous captures and filter to list only the protocol you are looking for, e.g. put arp in the filter box

    Apply this filter by selecting apply.

    Based on the filtered output above, draw up a three-column table in Microsoft Excel (or equivalent) containing the name, description and, position within the OSI Model of each of the following protocols:

    * DHCP (bootp)
    * ARP
    * DNS
    * Ethernet
    * HTTP
    * ICMP
    * IP
    * TCP
    * TLSv2 (SSL)

</details>