# what is NFS

The Network File System (NFS) is a mechanism for storing files on a network. It is a distributed file system that allows users to access files and directories located on remote computers and treat those files and directories as if they were local


NFS setup and installation in ubuntu
[for sever machine]
----------------------
step1: Update the System

 sudo apt update && sudo apt upgrade -y

step2: Install NFS Server:

 sudo apt install nfs-kernel-server -y

step3: create diretory with you want to share with others

 sudo mkdir -p /mnt/nfs_share

step4: Set appropriate permissions (modify as needed)

 sudo chown nobody:nogroup /mnt/nfs_share
 sudo chmod 777 /mnt/nfs_share

step5: Configure the Exported Directory

 sudo vim  /etc/exports

step6: Add the following line to export the directory:

  /mnt/nfs_share *(rw,sync,no_subtree_check)  NOTE: Replace * with specific client IP(s) or CIDR ranges for better security
  rw: Stands for Read/Write

  sync: Requires changes to be written to the disk before they are applied
  
  No_subtree_check: Eliminates subtree checking


step7: Apply the Configuration

 sudo exportfs -a

step8: Restart the NFS server

  sudo systemctl restart nfs-kernel-server

[for client machine]

step1: Install NFS Client (on Client Machine)

 sudo apt update
 
 sudo apt install nfs-common

step2: Mount the NFS Share (on Client Machine)

 sudo mkdir -p /mnt/nfs_client

step3: Mount the NFS share

 sudo mount <server-ip>:/mnt/nfs_share /mnt/nfs_client

step4: Verify the mount

 df -h

step5: On the client, use the showmount command to confirm the NFS server is exporting the directory correctly:

 showmount -e  <ip address>


note: On which port does nfs run:

(1) 2049	
(2)  111
How to check port used by service:
sudo netstat -tuln | grep 2049
sudo netstat -tuln | grep 111

Note:   In AWS, the service that provides NFS (Network File System) functionality is Amazon Elastic File System (EFS)

NFS (Network File System) is used to allow multiple systems or servers to share and access files over a network as if they were on a local disk. 

