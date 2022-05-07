Extended LVM partition
======================

### List physical partions
```
fdisk -l
Disk /dev/sda: 32.2 GB,
Disk /dev/mapper/vg_vmware-lv_root: 29.6 GB, 29569843200 bytes
Disk /dev/mapper/vg_vmware-lv_swap: 2113 MB, 2113929216 bytes
```

-------------------------------------------------------------------

```
df -lh

/dev/mapper/vg_vmware-lv_root        28G   15G   12G  57% /

increase the “physical” size of our disk 
fdisk -l
Disk /dev/sda: 64.4 GB,
Disk /dev/mapper/vg_vmware-lv_root: 29.6 GB, 
```

--------------------------------------------------------------------

```
fdisk /dev/sda
p   primary partition (1-4)
p
Partition number (1-4): 3

Command (m for help): w


fdisk -l
Disk /dev/sda: 64.4 GB, 64424509440 bytes
/dev/sda3            3917        7832    31453260   83  Linux
```


---------------------------------------------------------------------

```
pvdisplay
PV Name               /dev/sda2
PV Size               29.51 GiB 
 
 
pvcreate /dev/sda3
  Physical volume "/dev/sda3" successfully created
  
```

---------------------------------------------------------------------

```
pvdisplay

PV Name               /dev/sda2
VG Name               vg_vmware
 
PV Name               /dev/sda3
PV Size               30.00 GiB
```

----------------------------------------------------------------------------

```
vgdisplay | grep Name
VG Name               vg_vmware
```
--------------------------------------------------------------------------

```
vgextend vg_vmware /dev/sda3

Volume group "vg_vmware" successfully extended
```

---------------------------------------------------------------------

```
vgdisplay
 VG Size               59.50 GiB
```
---------------------------------------------------------------------------

```
lvdisplay | grep Path

 LV Path                /dev/vg_vmware/lv_root
```

-------------------------------------------------------

```
lvextend -l +100%FREE /dev/vg_vmware/lv_root
  Extending logical volume lv_root to 57.53 GiB
```
 ----------------------------------------------------

```
  lvdisplay
  LV Name                lv_root
  
   LV Size                57.53 GiB
```
------------------

```
    resize2fs /dev/vg_vmware/lv_root 
``` 
