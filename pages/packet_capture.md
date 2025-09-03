---
permalink: /packet-capture
---

# Packet Capture


Complete the following activities starting and stopping the packet capture as requested. Steps prefaced with "Issue command" are executed in the terminal.

<details>
    <summary>Capture 1</summary>
    <ol>
        <li>Issue command</li>
            <ul>
                <li>Windows from Administrator Powershell: <code>Remove-NetNeighbor *</code></li>
                <li>Linux: <code>sudo ip neigh flush all</code></li>
                <li>MacOS: <code>sudo arp -a -d</code></li>
            </ul>
        <li>Start Capture</li>
        <li>Issue command:</li>
            <ul>
                <li>Windows from Administrator CMD: <code>ping -n 5 www.google.ca</code></li>
                <li>Windows from Administrator Powershell: <code> Test-Connection -Count 5 www.google.ca</code></li>
                <li>Linux: <code>ping -c 5 www.google.ca</code></li>
                <li>MacOS: <code>ping -c 5 www.google.ca</code></li>
                <li>Stop Capture</li>
            </ul>
        <li>Save as <b>Capture1.pcap</b></li>
    </ol>
</details>

<details>
    <summary>Capture 2</summary>
    <ol>
        <li>Clear the cache from firefox / chrome / edge (<code>Ctrl+Shift+Delete</code>)</li>
        <li>Start capture</li>
        <li>Using a web browser visit <code>http://www.undeadly.org</code></li>
        <li>Stop Capture</li>
        <li>Save as <b>Capture2.pcap</b></li>
    </ol>
</details>

<details>
    <summary>Capture 3</summary>
    <ol>
        <li> Start capture</li>
        <li> Issue command:</li>
            <ul>
                <li> Windows from Administrator Powershell: <code>ipconfig /renew</code></li>
                <li> Linux: <code>sudo dhclient -r -pf /var/run/dhclient-em1.pid</code></li>
                <li> Stop capture</li>
            </ul>
        <li> Save as <b>Capture3.pcap</b></li>
    </ol>
</details>

<details>
    <summary>Analysis</summary>
    <p>Reload each of the previous captures and filter to list only the protocol you are looking for, e.g. put arp in the filter box</p>
    <p>Apply this filter by selecting apply.</p>
    <p>Based on the filtered output above, draw up a three-column table in Microsoft Excel (or equivalent) containing the name, description and, position within the OSI Model of each of the following protocols:</p>
    <ul>
    <li> DHCP (bootp)</li>
    <li> ARP</li>
    <li> DNS</li>
    <li> Ethernet</li>
    <li> HTTP</li>
    <li> ICMP</li>
    <li> IP</li>
    <li> TCP</li>
    <li> TLSv2 (SSL)</li>
    </ul>
</details>