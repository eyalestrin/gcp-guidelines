# Best practices for securing GCP Projects

## Configure MFA (Multi-Factor Authentication) for any account with owner privileges

In-order to avoid potential compromise of credentials, it is recommended to configure multi-factor authentication for any account with project owner privilege.

1. Install Google Authenticator, as instructed on:

   https://support.google.com/accounts/answer/1066447

   https://apps.apple.com/us/app/google-authenticator/id388497605

2. Login to the Google Account console:

   https://myaccount.google.com/

3. From the left pane, click on Security

4. Under "Signing in to Google", click on 2-Step Verification

5. Click on "Get started"

6. Enter your Google G Suite or Gmail password

7. Under "Authenticator app", click on Set Up

8. Choose which phone you have and click Next

9. From your mobile device, click Scan a barcode

10. Scan the barcode

11. Click Next

12. Enter the code shown on the Google Authenticator app on your phone

13. Click Verify

14. Click Done



## Limit number of inbound ports

Allowing large number of inbound ports access GCP resources increase the chance of network breach. Limit the number of inbound ports to required ports only and to specific resources or specific subnets.

1. Login to the Firewall rules page:

   https://console.cloud.google.com//networking/firewalls/list

2. From the upper pane, select an existing GCP Project

3. Review the list of existing Firewall rules, specifically rules with filter "IP ranges: 0.0.0.0/0"

   Note: It is highly recommended that inbound access on SSH (port 22TCP) or RDP (port 3389TCP) will be limited to specific IP address or IP range from known source location.

4. Update Firewall rules as needed.

5. Log off the GCP Management console.



## Google cloud storage permissions

Allowing public access to Google cloud storage buckets increase the chance of data breach. Make sure no Google cloud storage bucket is publicly accessible.

1. Open the Cloud Storage browser:

   https://console.cloud.google.com/storage/browser

2. From the upper pane, select an existing GCP Project

3. Review the list of existing Cloud storage buckets

4. Check each bucket under "Public access" field, and make sure no bucket is configured as "Public to internet"

5. Configure buckets as needed.

6. Log off GCP Management console.