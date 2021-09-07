Summary

Run df -h to verify your root partition is full (100%)  
Run lsblk and then lsblk -f to get block device details  
## if you cant growpart right away you can add volum to /tmp with this command   
sudo mount -o size=10M,rw,nodev,nosuid -t tmpfs tmpfs /tmp   


sudo growpart /dev/DEVICE_ID PARTITION_NUMBER  
lsblk to verify partition has expanded   
sudo resize2fs /dev/DEVICE_IDPARTITION_NUMBER  
Run df -h to verify your resized disk  
sudo umount /tmp  

