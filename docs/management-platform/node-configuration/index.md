# Node Configuration

Click on **Node** -> **Node Settings** to configure the current node information. This page is mainly used to configure the node's name, web server port.

![alt text](12.png)


| **Name**        | **Description**   |
|-----------------|-------------|
| Node Name       | The name of the current node. The node name is used as the unique identifier of the node during networking. The letters used in the name are case sensitive. If redundancy is enabled on the current node, the node name of the master and backup nodes should be the same, and the node name of the redundant node needs to be manually changed to the node name of the master node.    <br> **Note**: After the nodes form a network or redundancy, it is not recommended to modify the node name, which will affect the collection of historical data.  |
| Server Language | The server-side language of the VC Hub program.  |
| HTTP Port       | Default 8066, supports modification to configure the HTTP port for the web service.  |
| HTTPS Port      | Default 10043, support modification, configure the HTTPS port of the web service.  |
| Public Address  | Network address for the external network, mainly used for runtime page master-backup switchover.  |

