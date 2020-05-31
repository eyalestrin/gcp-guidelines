# How to create a GCP subnet

1. Login to the VPC network console:

   https://console.cloud.google.com//networking/networks/list

2. Select the relevant VPC network name

3. Click on "Add subnet"

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

4. Click on Add

5. Logoff the Google Cloud Platform management console

   