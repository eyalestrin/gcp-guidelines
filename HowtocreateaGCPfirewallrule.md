# How to create a GCP firewall rule

1. Login to the Firewall rules page:

   https://console.cloud.google.com//networking/firewalls/list

2. Click on "Create Firewall Rule"

   + **Name**: Specify here a name for the new firewall rule (in lowercase)

   + **Network**: Select the relevant Google Virtual Private Cloud (VPC) Network

   + **Priority**: Specify the Priority of the rule

     Note: The lower the number, the higher the priority

   + **Direction of traffic**: Choose either ingress (inbound traffic) or egress (outbound traffic)

   + **Action on match**: Choose either allow or deny

   + **Targets**: Select "All instances in the network" (destination of the specific firewall rule)

     For more information, see: 

     https://cloud.google.com/vpc/docs/firewalls#rule_assignment

   + **Source filter**: Select "IP ranges"

   + **Source IP ranges**: Specify the organization public IP subnet range or specify public IP CIDR

     For more information, see:

     https://cloud.google.com/vpc/docs/firewalls

   + **Protocols and ports**: Specify the relevant destination port (for example: tcp:22)

     For more information, see:

     https://cloud.google.com/vpc/docs/firewalls#protocols_and_ports

3. Click on "Create"

4. Logoff the Google Cloud Platform management console