---
permalink: /review/scenario-one
---

# Network Configuration - Scenario I

- **Task**: 
  - Attach **r1** to a new network named **test_net1** and configure it such that hosts within the new network obtain their IP address dynamically and are able to communicate with any destination.

## Diagram

![scenario one](../img/review/network_config_scenario_one.png)


## Details

- Configure **r1** as a DHCP server for the **test_net1** network using the following IP range:
  - **192.168.10.64/26**
- Configure **r1** to advertise a route to **test_net1** to neighbouring routers
- Verify that you can reach hosts within **test_net1** network from elsewhere in your topology
  
## Clean-up

Delete the **test_net1** network and associated configurations.