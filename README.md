# Automation-with-Ansible-UDP-Loadbalancing

In this work, a load balancer called HAproxy is set up and a Python Flask app is implemented.With the hostname and current time, the Flask application responds to requests.

Three development servers are employed to manage heavy demand, and HAproxy is utilised to load-balance them. To access the internal network through SSH, a Bastion host is used.A playbook called site.yaml from ansible is supplied to deploy the setup. 

The playbook runs outside the site but via the Bastion host and presupposes that the hosts are already configured. The Bastion host has to be configured with SSH in order to be used as a jump host, and all hosts require the usage of SSH keys for secure access. A fundamental function test is also included in the playbook to ensure that all development servers are functioning properly.

On the development servers, SNMPd daemon is further deployed for monitoring.

Nginx is used to handle SNMP traffic because HAproxy cannot support UDP. While HAproxy handles HTTP traffic on port 80, Nginx is set up as a UDP load balancer to handle SNMP traffic coming from the internet on port 1611.

The development servers hidden behind the load balancer, HAproxy and Nginx serving as entry points, and the Bastion host providing secure access make up the logical network/service map.
