---
permalink: /review/scenario-three
---

# Network Configuration - Scenario III

- **Task**: 
  - Create a new router named **test_rtr2** and attach it to the **net2** network. Additionally, attach **test_rtr2** to a new network named **test_net3** and configure it such that hosts within the new network obtain their IP address dynamically and are able to communicate with any destination.

## Diagram

![scenario one](../img/review/network_config_scenario_three.png)


## Details

- Configure **test_rtr2** as a DHCP server for the **test_net3** network using the following IP range:
  - **192.168.30.0/28**
- Enable routing in **test_rtr2** and configure it to advertise a route to **test_net3** to neighboring routers.
- Verify that you can reach hosts within **test_net3** network from elsewhere in your topology
  
## Clean-up

Delete **test_rtr2** and all the hosts within **test_net3** network.
