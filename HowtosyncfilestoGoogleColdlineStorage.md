# How to sync files to Google Coldline Storage

## Creating a storage bucket

1. Open the Cloud Storage browser:

   https://console.cloud.google.com/storage/browser

2. Click on "Create bucket":

   + **Name your bucket**: Specify here the bucket name (all lowercase, numbers and “-“ or “_”)

     Note: Do not specify sensitive information on the bucket name since it is searchable via DNS

   + **Choose a default storage class**: Select Coldline

   + **Location**: Select a close location, such as Europe-west2 (London)

   + **Choose how to control access to objects**: Leave the default settings

   + **Advanced settings:** Leave the default settings (Google-managed key)

3. Click on Create



## Google Cloud SDK installation phase

1. Login to a machine using privileged account

2. Install Google Cloud SDK tools.

   + Linux (Debian / Ubuntu):

     https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu

   + Linux (CentOS / RedHat):

     https://cloud.google.com/sdk/docs/quickstart-redhat-centos

   + Windows:

     https://cloud.google.com/sdk/docs/quickstart-windows

3. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

4. Select a GCP project from the list
5. Select a default Compute region and zone



## Common Google Cloud SDK CLI Commands

+ Login to Google Cloud Platform:

  `gcloud auth application-default login --no-launch-browser`

  Note: The command prompt will show you a link – copy the link to a new browser, login with your GCP project credentials and copy the verification code from the browser to the command prompt

+ List all active GCP accounts:

  `gcloud auth list`

+ Change the active account:

  `gcloud config set account <Account_Name>`

  Note: Replace **<Account_Name>** with the target GCP account

+ Lists all available GCP projects:

  `gcloud projects list`

+ Change the GCP project:

  `gcloud config set project "<Project_ID>"`

  Note: Replace **<Project_ID>** with the target GCP project ID



## Backup phase

1. List all Google Cloud Storage buckets inside the current GCP project:

   `gsutil ls -p “<Project_ID>”`

   Note: Replace **<Project_ID>** with the target GCP project ID

2. Run the command below (one time) to enable file versioning:

   `gsutil versioning set on gs://<bucketname>`

   Note: Replace **<bucketname_>** with the target bucket name

3. Run the command below to sync recursively the content of /data folder into a target bucket:

   `gsutil rsync -r /data gs://<bucketname>/target_folder`

   Note 1: Replace **/data** with the relevant source folder name

   Note 2: Replace **<bucketname_>** with the target bucket name

   Note 3: Replace **/target_folder** with the relevant target folder name



## References

+ Quickstart: Using the gsutil tool

  https://cloud.google.com/storage/docs/quickstart-gsutil

+ rsync - Synchronize content of two buckets/directories

  https://cloud.google.com/storage/docs/gsutil/commands/rsync

+ Easy, cheap and secure backup with Google Cloud Platform

  https://scotthelme.co.uk/easy-cheap-and-secure-backup-with-google-cloud-platform/

+ Top gsutil command lines to get started on Google Cloud Storage

  https://alexisperrier.com/gcp/2018/01/01/google-storage-gsutil.html

+ Use Cases and Different Ways to get Files Into Google Cloud Storage

  https://medium.com/google-cloud/use-cases-and-a-few-different-ways-to-get-files-into-google-cloud-storage-c8dce8f4f25a

+ Google Cloud Storage backup tutorial

  https://gist.github.com/rnwolf/533bf309bd84982c4b39d1ca7c03991f