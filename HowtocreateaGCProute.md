# How to create a GCP route

1. Login to the Route page:

   https://console.cloud.google.com//networking/routes/list

2. Click on "Create Route"

   + **Name**: Specify here a name for the new route (in lowercase)

   + **Network**: Select the relevant Google Virtual Private Cloud (VPC) Network

   + **Destination IP range**: Specify here the destination IP address CIDR

     For more information, see:

     https://cloud.google.com/vpc/docs/routes

   + **Priority**: Leave the default settings

   + **Next hop**: Select the relevant type

     For more information, see:

     https://cloud.google.com/vpc/docs/routes#routeselection

3. Click on "Create"

4. Logoff the Google Cloud Platform management console