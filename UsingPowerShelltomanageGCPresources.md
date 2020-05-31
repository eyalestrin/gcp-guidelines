# Using PowerShell to manage GCP resources

## How to configure PowerShell for managing GCP resources (Windows platform)

1. Login to the machine using privileged account.

2. Follow the instructions below to install the latest build of PowerShell:

   https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7

3. From command prompt, run the command below to invoke PowerShell:

   `pwsh`

   Note: You need to run cmd.exe or pwsh.exe as administrator.

4. Run the command below to find out the current PowerShell version:

   `$PSVersionTable.PSVersion`

5. In-case you currently have version older than 5.1, follow the article below to locate the download URL for upgrading to the latest version of PowerShell:

   https://docs.microsoft.com/en-us/powershell/scripting/install/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7

6. Run the command below to install Cloud SDK tools for PowerShell:

   `Install-Module -Name GoogleCloud -Force`

7. List all available cmdlets of Google Cloud PowerShell SDK:

   `Get-Command -CommandType Cmdlet -Module GoogleCloud*`

8. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-windows

9. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

10. Select a GCP project from the list

11. Select a default Compute region and zone


## How to configure PowerShell for managing GCP resources (RHEL/CentOS platform)

1. Login to the machine using privileged account.

2. Run the command below to register the RedHat 7 or CentOS 7 repository:

   `curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo`

3. Run the command below to install PowerShell:

   `sudo yum install -y powershell`

4. From command prompt, run the command below to invoke PowerShell:

   `sudo pwsh`

5. Run the command below to find out the current PowerShell version:

   `$PSVersionTable.PSVersion`

6. Run the command below to install Cloud SDK tools for PowerShell:

   `Install-Module -Name GoogleCloud -Force`

7. List all available cmdlets of Google Cloud PowerShell SDK:

   `Get-Command -CommandType Cmdlet -Module GoogleCloud*`

8. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-redhat-centos

9. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

10. Select a GCP project from the list

11. Select a default Compute region and zone

## How to configure PowerShell for managing GCP resources (Ubuntu 18.04 platform)

1. Login to the machine using privileged account.

2. Run the command below to register the Ubuntu 18.04 repository:

   `wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb`

   `sudo dpkg -i packages-microsoft-prod.deb`

   `sudo apt-get update`

   `sudo add-apt-repository universe`

3. Run the command below to install PowerShell:

   `sudo apt-get install -y powershell`

4. From command prompt, run the command below to invoke PowerShell:

   `pwsh`

5. Run the command below to find out the current PowerShell version:

   `$PSVersionTable.PSVersion`

6. Run the command below to install Cloud SDK tools for PowerShell:

   `Install-Module -Name GoogleCloud -Force`

7. List all available cmdlets of Google Cloud PowerShell SDK:

   `Get-Command -CommandType Cmdlet -Module GoogleCloud*`

8. Install Google Cloud SDK, as instructed below:

   https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu

9. Run the following from command prompt to initialize the Cloud SDK:

   `gcloud init --console-only`

10. Select a GCP project from the list

11. Select a default Compute region and zone



## Common PowerShell commands for GCP

+ Login to Google Cloud Platform:

  `gcloud auth login --no-launch-browser`

+ List all active GCP accounts:

  `gcloud auth list`

+ Change the active account:

  `gcloud config set account <Account_Name>`

  Note: Replace **<Account_Name>** with the target GCP account

+ Lists all available GCP projects:

  `Get-GcpProject | select Name,ProjectId`

+ Change the GCP project:

  `gcloud config set project “<Project_ID>”`

  Note: Replace **<Project_ID>** with the target GCP project ID



## Network related commands

+ List available networks:

  `Get-GceNetwork | select Name,AutoCreateSubnetworks,IPv4Range,GatewayIPv4`

+ Create a new network inside a specific GCP project:

  `New-GceNetwork -Name "my-network" -IPv4Range <CIDR_Block> -Project "my-project"`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **my-network** with the relevant network name

  Note 3: Replace **<CIDR_Block>** with the relevant value (such as 10.240.0.0/16)

  Note 4: Replace **my-project** with the target GCP project ID

+ Delete a network inside a specific GCP project:

  `Remove-GceNetwork -Network "my-network" -Project "my-project"`

  Note 1: Replace **my-network** with the relevant network name

  Note 2: Replace **my-project** with the target GCP project ID



## Firewall rules related commands

+ List all available Firewall rules inside a GCP project:

  `Get-GceFirewall -Project "my-project" | select Name,Direction,Priority,Allowed,Denied`

  Note: Replace **my-project** with the target GCP project ID

+ List settings of a specific Firewall rule inside a GCP project:

  `Get-GceFirewall "my-firewall" -Project "my-project"`

  Note 1: Replace **my-firewall** with the specific firewall rule name

  Note 2: Replace **my-project** with the target GCP project ID

+ Create a new Web allow firewall rule:

  `New-GceFirewallProtocol tcp -Port 80 | Add-GceFirewall -Project "my-project" -Name "rule-name" -Network "my-network" -Description "Allow Web Traffic"`

  Note 1: The above commands should be written as a single line

  Note 2: Replace **80** with the target port number

  Note 3: Replace **my-project** with the target GCP project ID

  Note 4: Replace **rule-name** with the target rule name

  Note 5: Replace **my-network** with the relevant network name

  Note 6: Replace **"Allow Web Traffic"** with a relevant rule description



## VM Instance related commands

+ List all available VM instances in the current GCP project:

  `Get-GceInstance`

+ List available VM instance image types, sorted by Name and Family:

  `Get-GceImage | Format-Table Name,Family`

+ List all machine types:

  `Get-GceMachineType | Format-Table Name,Zone,GuestCpus,MemoryMb,Deprecated`

+ Create a new CentOS 7 VM instance:

  `$disk = Get-GceImage "centos-cloud" -Family "centos-7"`

  `$config = New-GceInstanceConfig "my-sample-vm" -MachineType "n1-standard-1" -Region europe-west2 -DiskImage $disk`

  `$config | Add-GceInstance -Project "my-project" -Zone "europe-west2-a"`

  Note 1: The second command should be written as a single line

  Note 2: Replace **centos-cloud** with the relevant Image-project

  Note 3: Replace **centos-7** with the relevant Image-family

  Note 4: Replace **my-sample-vm** with the target VM instance hostname

  Note 5: Replace **n1-standard-1** with the relevant VM instance type, from the list:

  https://cloud.google.com/compute/docs/machine-types

  Note 6: Replace **europe-west2** with the target region

  Note 7: Replace **my-project** with the target GCP project ID

  Note 8: Replace **europe-west2-a** with the target zone

+ Get information about specific VM instance in a specific zone:

  `Get-GceInstance "my-instance" -Project "my-project" -Zone "europe-west2-a"`

  Note 1: Replace **my-instance** with the target VM instance hostname

  Note 2: Replace **my-project** with the target GCP project ID

  Note 3: Replace **europe-west2-a** with the target zone

+ Start VM instance in a specific zone:

  `Start-GceInstance -Name "my-instance" -Project "my-project" -Zone "europe-west2-a"`

  Note 1: Replace **my-instance** with the target VM instance hostname

  Note 2: Replace **my-project** with the target GCP project ID

  Note 3: Replace **europe-west2-a** with the target zone

+ Restart VM instance in a specific zone:

  `Restart-GceInstance -Name "my-instance" -Project "my-project" -Zone "europe-west2-a"`

  Note 1: The second command should be written as a single line

  Note 2: Replace **my-instance** with the target VM instance hostname

  Note 3: Replace **my-project** with the target GCP project ID

  Note 4: Replace **europe-west2-a** with the target zone

+ Stop VM instance in a specific zone:

  `Stop-GceInstance -Name "my-instance" -Project "my-project" -Zone "europe-west2-a"`

  Note 1: Replace **my-instance** with the target VM instance hostname

  Note 2: Replace **my-project** with the target GCP project ID

  Note 3: Replace **europe-west2-a** with the target zone



## Storage related commands

+ List all Google Cloud Storage buckets inside the current GCP project:

  `Get-GcsBucket -Project "<Project_ID>" | select Name`

  Note: Replace **<Project_ID>** with the target GCP project ID

+ Create a new Google Cloud Storage bucket:

  `New-GcsBucket -Name "my-bucket" -Project "<Project_ID>"`

  Note 1: Replace **my-bucket** with the target bucket name

  Note 2: Replace **<Project_ID>** with the target GCP project ID

+ Remove Google Cloud Storage bucket:

  `Remove-GcsBucket "my-bucket" -Force`

  Note: Replace **my-bucket** with the target bucket name