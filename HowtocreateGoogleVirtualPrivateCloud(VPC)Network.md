# How to create Google Virtual Private Cloud (VPC) Network

1. Login to the VPC network console:

   https://console.cloud.google.com//networking/networks/list

2. From the upper pane, click on "Create VPC Network":

   + **Name**: Specify a name for the new VPC (in lowercase)

   + **Subnet creation mode**: Select "Custom":

     + **Name**: Specify a name for the new subnet (in lowercase)

     + **Region**: Select a region close to your location

     + **IP address range**: Specify the CIDR block according to your needs

       Note: For more information about network subnets, see:

       https://cloud.google.com/vpc/docs/vpc#vpc_networks_and_subnets

     + **Private Google access**: Leave the default settings (Off)

       For more information, see:

       https://cloud.google.com/vpc/docs/private-google-access

     + **Flow logs**: Leave the default settings (Off)

       For more information, see:

       https://cloud.google.com/vpc/docs/using-flow-logs

3. Click on Done

4. In-case needed, add additional subnets to the VPC

5. **Dynamic routing mode**: Leave the default settings (Regional)

   For more information, see:

   https://cloud.google.com/router/docs/how-to/configuring-routing-mode

6. Click on "Create"

7. Logoff the Google Cloud Platform management console