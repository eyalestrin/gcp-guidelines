# How to configure Google Cloud Storage bucket

1. Open the Cloud Storage browser:

   https://console.cloud.google.com/storage/browser

2. Click on "Create bucket":

   + **Name**: Specify here the bucket name

   + **Default storage class**: Choose "Regional Storage"

     For more information, see:

     https://cloud.google.com/storage/docs/storage-classes

   + **Location:** Select a region close to your location

3. Click on "Show advanced settings"

4. Under "Labels", click on "Add label":

   + **Key** – Specify here "name" (in lower case)

   + **Value** - Specify here the bucket name

     For more information, see:

     https://cloud.google.com/storage/docs/using-bucket-labels

   + **Encryption** - Leave the default settings (Google-managed key)

5. Click on Create