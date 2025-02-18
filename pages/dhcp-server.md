---
permalink: /project-dhcp-server
---
# DHCP Server

This activity configures a DHCP service in __r1__ and __r2__ which will handle IP configuration requests from __net1__ and __net2__ subnets respectively.

When completed, hosts within __net1__ and __net2__ subnets (`web`, `ws1`,` ws2`) will have their network settings configured dynamically via DHCP.

## Deliverable

![dhcp server](../img/project/dhcp_server.png)

## Setup

Ensure __web__, __ws1__ and __ws2__ are configured to obtain their IPv4 configuration dynamically; i.e. remove their statically assigned IPv4 addresses and set their configuration method to be automatic.

You will need to use the __nmtui__ tool to achieve this.

<br />
<br />

> [!IMPORTANT] Configuration steps
> In general, there are three steps involved in provisioning  a service on Linux:
>
>Edit configuration file (typically located under the `/etc/` directory)
>Validate configuration file - check for any syntax errors
>Enable and start the service - often by leveraging the `systemd` framework

<br />

## Edit configuration file

The dhcpd service listens to requests based on the subnets declarations inside the `/etc/dhcp/dhcpd.conf` file. In both __r1__ and __r2__, find this file and open it using your preferred text editor, and add configuration options to allocate addresses as described in the diagram.

An example configuration is given below (this is only an example; your configuration must use the IP subnets specified in the diagram):

<details>
<summary>Example <code>dhcpd.conf</code> file</summary>

<pre><code>
# /etc/dhcp/dhcpd.conf

# DHCP Server Configuration file.
#   see /usr/share/doc/dhcp-server/dhcpd.conf.example
#   see dhcpd.conf(5) man page
# Global options
# option domain-name "2620.acit";
option domain-name-servers 8.8.8.8, 10.20.30.254;

subnet 192.168.15.0 netmask 255.255.255.128 {
	# routers option defines the default gateway for clients
	option routers 192.168.15.126;

	# range specifies the start and end of address range
        # this will provision a range of 40 addresses
	range 192.168.15.10 192.168.15.50;	
}

# the host declaration is a container for the configuration
# of a specific host. The name is arbitrary but generally
# the same as the hostname.

host host1 {
	# the hardware statement is used to match the MAC address
	# of a particular host 
	hardware ethernet 02:00:00:00:00:03;

	# fixed address is used to consistently assign an IP address
	# to the host specified by the MAC address given above.
	fixed-address 192.168.15.1;
}

host host2 {
	hardware ethernet 02:00:00:00:00:04;
		
	fixed-address 192.168.15.2;
}    
</code></pre>
</details>

## Enable and start the service

1. Check syntax errors: 

```bash 
sudo dhcpd -t
```

2. Start the service: 

```bash
sudo systemctl start dhcpd.service
```

3. Enable the service to always start at boot: 

```bash
sudo systemctl enable dhcpd.service
```

## Add routes on your Windows workstation

To be able to log into your __net1__ and __net2__ hosts from your host, you need to add routes.

Run the following command in Powershell as administrator to add a route to __net1__:

```pwsh
New-NetRoute -DestinationPrefix "172.16.1.0/27" -InterfaceIndex $index -NextHop 10.20.30.100
```

where `$index` is the interface index of your __Host-Only Ethernet Adapter #2__ (hint: run `Get-NetAdapter` to find out the index value)

For convenience, you may also update your `./ssh/config` file with login credentials for __web__ and __ws1__.

> [!TIP] macOS users
> If you are on a mac, you may need to do a bit of internet search to find out how to add routes permanently on your system. 
> This [blog post](https://www.analysisman.com/2020/11/macos-staticroutes.html) might provide answers (I can't guarantee that it works on all mac versions)

## Troubleshooting

- Before starting the service, ensure there are not syntax errors by running: `sudo dhcpd -t`.
- Ensure the subnet declarations in your configuration files match those in your topology.
- Check service status: `systemctl status dhcpd.service`
- To check logs messages while the service is running: `journalctl -u dhcpd`