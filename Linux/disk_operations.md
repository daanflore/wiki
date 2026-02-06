how does lvm work:
![[lvm.png]]

# scan devices
In case an added disk is not visible you can scan it with the following command:
```bash
 ls -1 /sys/class/scsi_device 
 echo 1 > /sys/class/scsi_device/2\:0\:0\:0/device/rescan
```

# check disk size and free

command
```bash
sudo ssm list
```

# extend volume
```bash
sudo ssm resize -s +5G /dev/alma/var
```

# extend device
```bash
sudo growpart /dev/sd[a-b] {number of disk}
sudo pvresize /dev/sd[a-b][1-9]

# Example
# Will increase the size of the first partition on the disk adn then resize the pv
sudo growpart /dev/sdb 1
sudo pvresize /dev/sdb1
```

# Adding new disk

```bash
[fdisk (for MBR)|gdisk (for GPT)] /dev/sdx    
Command: n (new)
Partition1 (if new disk)    
p  
1   
t 
8e ( Om naar LVM te gaan ) 8e00 (if using gdisk)   
p   (print for validaiton)
w   (write to system)
df -h 
sudo ssm add -p alma /dev/sdXX 
ssm create -s 1T -n /dev/centos/oracle07 --fstype xfs -p centos 
mkfs.xfs /dev/centos/oracle07 
vi /etc/fstab 
mkdir /oracle07 
mount /oracle07
```


List volume groups:
```sh
sudo vgdisplay
or
sudo vgs
```

List logical volumes:
```sh
sudo lvs
or
sudo lvdisplay
```

```sh
lsblk
```


List physical volumes:
```sh
sudo pvs
or
sudo pvdisplay
```