# Using Google Cloud SDK CLI Tools for managing GCP resources

## How to install Google Cloud SDK (Windows Platform)

1. Login to the machine using privileged account.

2. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-windows

3. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

4. Select a GCP project from the list
5. Select a default Compute region and zone



## How to install Google Cloud SDK (RHEL / CentOS Platform)

1. Login to the machine using privileged account.

2. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-redhat-centos

3. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

4. Select a GCP project from the list
5. Select a default Compute region and zone



## How to install Google Cloud SDK (Ubuntu/Debian Platform)

1. Login to the machine using privileged account.

2. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu

3. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

4. Select a GCP project from the list
5. Select a default Compute region and zone



## Common Google Cloud SDK CLI Commands

+ Login to Google Cloud Platform:

  `gcloud auth application-default login --no-launch-browser`

+ List all active GCP accounts:

  `gcloud auth list`

+ Change the active account:

  `gcloud config set account <Account_Name>`

  Note: Replace **<Account_Name>** with the target GCP account

+ Lists all available GCP projects:

  `gcloud projects list`

+ Change the GCP project:

  `gcloud config set project “<Project_ID>”`

  Note: Replace **<Project_ID>** with the target GCP project ID



## Network related commands

+ List available networks:

  `gcloud compute networks list`

+ Create a new network:

  `gcloud compute networks create my-network`

  Note: Replace **my-network** with the relevant network name

+ Delete a network:

  `gcloud compute networks delete my-network`

  Note: Replace **my-network** with the relevant network name

+ List available subnets:

  `gcloud compute networks subnets list`

+ Create a new subnet:

  `gcloud compute networks subnets create my-subnet --network=my-network --range=<Subnet address prefix CIDR> --region=region-name`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **my-subnet** with your own subnet name (in lower-case)

  Note 3: Replace **my-network** with the relevant network name

  Note 4: Replace **<Subnet_address_prefix_CIDR>** with the relevant value (such as 192.168.0.0/20)

  Note 5: Replace **region-name** with value from the list below:

  https://cloud.google.com/compute/docs/regions-zones/



## Firewall rules related commands

+ List all available Firewall rules inside a GCP project:

  `gcloud compute firewall-rules list`

+ List settings of a specific Firewall rule:

  `gcloud compute firewall-rules describe default-allow-ssh`

  Note: Replace **default-allow-ssh** with the target firewall rule name

+ Create a new RDP allow firewall rule:

  `gcloud compute firewall-rules create allow-rdp --allow tcp:3389 --description="Allow RDP"`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **allow-rdp** with your own rule name (in lower-case)

  Note 3: Replace **3389** with the target port number

  Note 4: Replace "Allow RDP" with your own rule description



## VM Instance related commands

+ List all available VM instances in the current GCP project:

  `gcloud compute instances list`

+ List available VM instance image types, sorted by Project and Family:

  `gcloud compute images list`

+ List all machine types:

  `gcloud compute machine-types list`

+ Create a new CentOS 7 VM instance:

  `gcloud compute instances create my-sample-vm --image-family centos-7 --image-project centos-cloud --zone europe-west2-a`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **my-sample-vm** with the target VM instance hostname

  Note 3: Replace **centos-7** with the relevant Image-family

  Note 4: Replace **centos-cloud** with the relevant Image-project

  Note 5: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/

+ Get information about specific VM instance in a specific zone:

  `gcloud compute instances describe my-sample-vm --zone europe-west2-a`

  Note 1: Replace **my-sample-vm** with the target VM instance hostname

  Note 2: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/

+ Show VM instance power state:

  `gcloud compute instances describe my-sample-vm --zone europe-west2-a --format='table(name,status)'`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **my-sample-vm** with the target VM instance hostname

  Note 3: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/

+ Start VM instance in a specific zone:

  `gcloud compute instances start my-sample-vm --zone europe-west2-a`

  Note 1: Replace **my-sample-vm** with the target VM instance hostname

  Note 2: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/

+ Restart VM instance in a specific zone:

  `gcloud compute instances reset my-sample-vm --zone europe-west2-a`

  Note 1: Replace **my-sample-vm** with the target VM instance hostname

  Note 2: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/

+ Stop VM instance in a specific zone:

  `gcloud compute instances stop my-sample-vm --zone europe-west2-a`

  Note 1: Replace **my-sample-vm** with the target VM instance hostname

  Note 2: Replace **europe-west2-a** with the target zone, from the list:

  https://cloud.google.com/compute/docs/regions-zones/



## Storage related commands

+ List all Google Cloud Storage buckets inside the current GCP project:

  `gsutil ls -p “<Project_ID>”`

  Note: Replace **<Project_ID>** with the target GCP project ID

+ Create a new Google Cloud Storage bucket:

  `gsutil mb -c regional -l europe-west2 gs://my-bucket -p “<Project_ID>”`

  Note 1: Replace **europe-west2** with the target region

  Note 2: Replace **my-bucket** with the target bucket name

  Note 3: Replace **<Project_ID>** with the target GCP project ID

+ Remove Google Cloud Storage bucket:

  `gsutil rm -r gs://my-bucket/`

  Note: Replace **my-bucket** with the target bucket name