# How to create GCP budget and billing alerts

1. Login to the GCP billing console:

   https://console.cloud.google.com/billing

2. From the left pane, click on Billing

3. Click on Go to linked billing account

4. From the left pane, click on Budget & alerts

5. Click on Create budget

   + **Name:** Budget policy for GCP Project <Project_Name>

     Note: Replace <Project_Name> with the relevant GCP Project name

   + **Projects:** Select the target GCP project name from the list

   + **Products:** All products

6. Click Next

   + **Budget type:** Specified amount
   + **Target amount:** Specify here the current balance (not the entire year!!!)
   + **Include credits in cost:** Leave selected

7. Click Next
   + Set budget alerts at 75%, 85% and 90%
8. Click Finish
9. Log off GCP console