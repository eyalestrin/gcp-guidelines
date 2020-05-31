# How to mount Google Cloud Storage inside a Linux machine

## Create credentials file

1. Login to the GCP console:

   https://console.cloud.google.com/

2. From the upper pane, select the target GCP project

3. Login to the link below to create a new service account key:

   https://console.cloud.google.com/apis/credentials/serviceaccountkey

4. Service account -> select New service account:

   + **Service account name:** Specify an informative name for the new service account
   + **Role:** Select Storage -> Storage object admin
   + **Key type:** JSON

5. Click on Create
6. Save the newly created JSON file in a secured location
7. Click on Close



## GCFuse installation

1. Login using SSH to the target Linux machine using privileged account.

2. Follow the instructions below to install the Cloud storage Fuse adapter:

   https://github.com/GoogleCloudPlatform/gcsfuse/blob/master/docs/installing.md

3. Copy the JSON file created above into **~/**

4. Rename the JSON file:

   `mv ~/Myfile.json ~/key.json`

   Note: Replace **Myfile.json** with the actual JSON file



## Mount phase

1. Run the commands below to mount the Google Cloud Storage:

   `sudo mkdir /dev/cloudstorage`

   `sudo chown MyUser:MyUser /dev/cloudstorage/`

   `sudo chmod 777 /dev/cloudstorage/`

   `gcsfuse --implicit-dirs --key-file ~/key.json StorageName /dev/cloudstorage`

   Note 1: Replace **MyUser** with the username you have logged into the Linux machine

   Note 2: Replace **StorageName** with the target Google storage bucket name

2. To view the content of the Google cloud storage bucket, switch to the new mount point:

   `cd /dev/cloudstorage`



## Unmount phase

1. When completing the work on the bucket, from the Linux SSH console, and run the commands below to unmount the Google Cloud Storage:

   `cd ~`

   `sudo fusermount -u /dev/cloudstorage`

2. Logoff the Linux machine



## Additional references regarding permanent mount using FSTAB

+ https://github.com/GoogleCloudPlatform/gcsfuse/blob/master/docs/mounting.md
+ https://reiners.io/mounting-google-cloud-buckets-in-centos/