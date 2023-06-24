---
id: qotq7hv49offs07okrs7mkc
title: 16-Storage media
desc: ''
updated: 1687208235168
created: 1686878800561
---

```BASH
mount        # Mount a file system
umount       # Unmount a file system
fsck         # Check and repair a file system
fdisk        # Manipulate disk partition table
mkfs         # Create a file system
dd           # Convert and copy a file
genisoimage  # (mkisofs) Create an ISO 9660 image file
wodim        # (cdrecord) Write data to optical storage media
md5sum       # Calculate an MD5 checksum
```

## Mounting and unmounting storage devices

The first step in managing a storage device is attaching the device to the file system tree. This process, called **mounting**, allows the device to interact with the operating system.  This contrasts with other operating systems such as Windows that maintain separate file system trees for each
device.

A file named `/etc/fstab` (short for "file system table") lists the devices (typically hard disk partitions) that are to be mounted at boot time.

| Field |     Contents     |                                                                                                                            Description                                                                                                                             |
|:-----:|:----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|   1   |      Device      | Traditionally, this field contains the actual name of a device file associated with the physical device. But with today's computers, which have many devices that are hot pluggable, many modern Linux distributions associate a device with a text label instead. |
|   2   |   Mount point    |                                                                                                The directory where the device is attached to the file system tree.                                                                                                 |
|   3   | File system tupe |                                                                                                         Linux allows many file system types to be mounted.                                                                                                         |
|   4   |     Options      |                                                                                                                                                                                                                                                                    |
|   5   |    Frequency     |                                                                                A single number that specifies if and when a file system is to be backed up with the `dump` command.                                                                                |
|   6   |      Order       |                                                                                A single number that specifies in what order file systems should be checked with the `fsck` command.                                                                                |

### Viewing a list of mounted file systems

Entering the `mount`command without arguments will display a list of the file systems currently mounted.

> The formating of the listing is as follows `<device> on <mount point> type <filesystem type> (<options>)`.

---

After inserting a CD-ROOM in a CentOS system.

```BASH
mount

# /dev/mapper/VolGroup00-LogVol00 on / type ext4 (rw)
# proc on /proc type proc (rw)
# sysfs on /sys type sysfs (rw)
# devpts on /dev/pts type devpts (rw,gid=5,mode=620)
# /dev/hda1 on /boot type ext4 (rw)
# tmpfs on /dev/shm type tmpfs (rw)
# none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
# sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
# /dev/sdc on /media/live-1.0.10-8 type iso9660 (ro,noexec,nosuid,nodev,uid=500)
```

The disk has been mounted on `/media/live-1.0.10-8`, path tha can be change with the following commands:

```BASH
su -
umount /dev/sdc # Unmounting the device
mkdir /mnt/cdrom
mount -t iso9660 /dev/sdc /mnt/cdrom
```

Now we can examine the contents of the CD-ROM via the new
mount point.

> If you want to unmount the device, make sure you aren't using it first.

### Determining device names

|   Patter   |                                           Device                                            |
|:----------:|:-------------------------------------------------------------------------------------------:|
| `/dev/fd*` |                                     Floppy disk drives.                                     |
| `/dev/hd*` |                             IDE (PATA) disks on older systems.                              |
| `/dev/lp*` |                                          Printers.                                          |
| `/dev/sd*` | SCSI disks.  On modern Linux systems, the kernel treats all disk-like devices as this type. |
| `/dev/sr*` |                        Optical drives (CD/DVD readers and burners).                         |

Using the `tail` command to monitor the `/var/log/messages` or `/var/log/syslog` file, we can know the name of a removable device when it is attached.

## Creating new file systems

### Manipulating partitions with fdisk