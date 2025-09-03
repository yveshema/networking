---
permalink: /ip-configuration
---

# Elements of a host's IP Configuration


In this activity you will explore the networking tools that let you discover IP configuration on both Windows and Linux. These tools give you information about your IP configuration and related settings which are key in troubleshooting IP networks.

1. IP configuration:
    - __Windows__
    On your Windows host, run the following commands to discover your network and IP configuration:
      - Display link-layer settings (Powershell): `Get-NetAdapter`
      - Display IP address: `Get-NetIPAddress`
      - Display IP configuration: `Get-NetIPConfiguration`
  
    - __Linux__
    Launch one of your virtual machines and run the following commands to find out its IP configuration
      - Display link-layer settings: `ip link show`
      - Display IP configuration: `ip addr show`

> [!TIP]
> Based on the output from the commands above, what are the elements of IP configuration?
>
> What is the meaning of each IP configuration item?

2. IP route tracing:

Run the following commands to trace the path an IP packet would traverse to each the following destinations:

> [!NOTE]
> The __$IP__ in the commands below refers to either the destination DNS name or IP address

- globalnews.ca
- 8.8.8.8
- On Windows, run: `Test-NetConnection $IP -traceroute`
- Alternatively, you can run: `tracert -d $IP` (the -d option causes tracert not to resolve domain names, thus making it faster).
- On Linux, run: `sudo traceroute -I $IP` (the -I option causes traceroute to use ICMP (the default is TCP) which is faster. You need root priviledges to use the option).

> [!TIP]
> Run:
> `Get-NetRoute -AddressFamily IPv4` on Windows, or
> `ip route show` on Linux
> to display the routing table. Are any of the intermediate routers listed in the tracert/traceroute output in the routing table?
>
> How did tracert/traceroute find out about all the intermediate routers between your computer and the packet destination?
