# What does this project do in detail?
I created this Ansible playbook mainly for educational purposes. I wanted to learn more about building a Kubernetes cluster on "bare metal" (onpremises VMs), CloudInit and managing complex environments via Ansible. This is the first larger project I created with Ansible, so there were many many learnings.

# How does the playbook make things easier?
It managed my onpremises Kubernetes cluster and makes it possible to easily add new Nodes or recreate the environment on a new host or as disaster recovery. The scaling is practically unlimited in horizontal scale, so I could easily scale the cluster out if the workload needs it.

## Process to add a Node
My current implementation of the Kubernetes cluster is running onpremises on a single Proxmox Node. I can clone the VM template I created, assign a hostname and change the IP address in the cloudinit drive. After that I can simply add the Node with it's hostname and IP to the inventory file on my Ansible control server in the group control or worker. The playbook will install Docker and Kubernetes, including all requirements and pin the specified Kubernetes version. After that it will join the Node to the cluster.

Running the playbook again does not change any configuration on the existing Nodes.

# Things to improve
- [ ] I learned that the roles feature of Ansible is the better fit for this purpose, so if I have time I will rewrite the project using these.
- [ ] Currently there is no implementation for removing a Node completely.
- [ ] The hostfile is currently not filled by the inventory, but the variabels specified on top
