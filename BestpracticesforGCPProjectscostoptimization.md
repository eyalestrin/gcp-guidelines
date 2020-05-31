# Best practices for GCP Projects cost optimization

## Unused Compute Engine Disks

1. Open the GCP Management console:

   https://console.cloud.google.com/compute/disks

2. From the upper pane, select an existing GCP Project

3. Review the list of existing Disks

4. Check each Disk under "In use by" field

5. In case a disk is not in use by any VM, select the disk and click Delete

6. Log off GCP Management console.



## Unused Virtual machines

1. Open the GCP Management console:

   https://console.cloud.google.com/compute/instances

2. From the upper pane, select an existing GCP Project

3. Review the list of existing VM instances

4. In case a VM instance is shutdown, review if the VM instance is needed.

5. If a VM instance is not needed, select the VM and click Delete

6. Log off GCP Management console.



## Unassociated External IP Addresses

1. Open the GCP Management console:

   https://console.cloud.google.com/networking/addresses/list

2. From the upper pane, select an existing GCP Project

3. Review the list of existing External IP addresses

4. In case an External IP address is not needed or not assigned to any resource, check the box next to the IP address to release.

5. Click Release IP address.

6. Log off GCP Management console.