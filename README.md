# start-scripts2
This repository is used in conjunction with a separate tarball and you should have received a link to download it. The deployment should consist of one master node and a minimum of two worker nodes.

Ensure that the master node and all worker nodes can communicate to each other freely. In other words, create a firewall rule that allows for communication between all nodes, on all ports and protocols.

The worker nodes should also have ports open for SSH and any ports in your environment used for management of the device / vm. The Master node should be configured the same as the worker node but it should also have TCP port 3000 and any port used to send logs. All logs should be sent to the master node.

On the master node, Clone this repository into the home directory of the username being used to install the system. Move the tarball into the start-scripts directory (do not extract it). Next, run the sliceinstall.sh script. Do not use sudo when executing this command. The script will prompt for sudo when required.

This deployment configuration is set up to run as a POC. If you start with a 1tb of SSD drive space on the master, your system will run for approximately 30 days (+/- 10 days) -  at 8k/sec of logs. For production usage, the system will have to be customized for your environment. This will include database cleaning and data retention policies. 

Also for production, certificates will need to be installed, HTTPS will need to be configured, and database configurations will need to be refined to enhance security and match policies.

These systems should start out with full and open communications between all devices in the cluster. Traffic that is not to or from the master/workers should be blocked for the worker nodes. The exception would be any protocols used for device administration. The master should allow the configured Syslog port, TCP port 3000, administration traffic, and full communication to the workers.
