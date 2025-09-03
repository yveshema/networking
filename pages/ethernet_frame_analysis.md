---
permalink: /ethernet-frame-analysis
---

# Activity: Ethernet Frame Analysis


## Part I

> [!NOTE]
> Before performing the following tasks, make sure that your virtual switch setup, i.e. launch Virtualbox and boot all your VM's > starting with the instructor router, followed by **r1** and **r2** and finally **web** and **ws1**.
>
> Verify that traffic is traversing the bridge in **r1**.

- Launch Wireshark
- Select **Capture** from the toolbar, and in the dropdown select options.
- In the dialog that pops up, select **`Virtualbox Host-Only Network #2`** from the interface list
- In the input box at the bottom of the dialog pane (labelled "**Capture filter for selected interfaces:**") type "`ether multicast`"
- Click on Start. The capture will begin. Let it run for about a minute, then stop the capture

> [!TIP]
> In the filter input box at the top of Wireshark window, type "stp" and press Enter
>
> - Select one of the filtered packets and examine it. Do you notice anything different in how Wireshark displays it?
> - What are the three fields of the ethernet header?
> - Examine the destination MAC address. Where did you see this address before?
> - Still looking at the destination MAC address, expand it and examine the contents inside. What type of address is it?
> - Similarly, examine the source MAC address. What are the characteristics of this address?
  
## Part II

- Log into each of **web**, **ws1**, **r1** and **r2** and flush the arp cache in each.
- Run <br /> `arp -n`  <br /> to display the arp entries
- Run <br /> `sudo ip -s -s neigh flush all` <br /> to delete all entries in the cache
  - Alternatively you can delete entries individually by running <br /> `sudo arp -d [ip_address]`
- In __ws1__, **r1** and **r2**, execute a packet capture as follows: <br /> `sudo tcpdump arp -w [capture_file_name]` <br /> where ``[capture_file_name]`` is `ws1_capture.pcap`, `r1_capture.pcap` and `r2_capture.pcap` for **ws1**, **r1** and **r2** respectively
- In __web__, send a few ping probes to __ws1__ and 8.8.8.8
- Stop the captures
- Copy the capture files to your host and examine them with Wireshark.
  - Create a folder on your host called "captures" in a suitable location, then in Powershell navigation to that folder just created.
  - In Powershell run: <br /> `scp admin@[vm_ip_address]:[capture_file_name] ./` <br /> to copy the specified capture file into the __"captures"__ folder (if you ssh configuration is set up correctly, you can run something like `scp r1:r1_capture.pcap ./` )
  - Alternatively, you may use __`sftp`__

> [!TIP]
> The three capture files each contain ARP packets even though the ping probes were only send to ws1 and google name server. Why?
>
> - Select one of the ARP packet and examine its contents.
> - What is the destination MAC address? What type of address is it?
> - What is the value of the __EtherType__ field?
> - Expand the contents of the ARP protocol:
> - What is the Protocol type? Why?
> - What is the __Target MAC address__? Notice anything unusual about it? Why?
