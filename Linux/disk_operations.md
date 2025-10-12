
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

# extend disk
```bash
sudo ssm resize -s +5G /dev/alma/var
```


# Adding new disk

```bash
[fdisk (for MBR)|gdisk (for GPT)] /dev/sdx    
n
1 (if new disk)    
p  
1   
t 
8e ( Om naar LVM te gaan ) 8e00 (if using gdisk)   
p   
w 
df -h 
sudo ssm add -p alma /dev/sdXX 
ssm create -s 1T -n /dev/centos/oracle07 --fstype xfs -p centos 
mkfs.xfs /dev/centos/oracle07 
vi /etc/fstab 
mkdir /oracle07 
mount /oracle07
```