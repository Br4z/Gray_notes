---
id: 3wy7im5ivrfigjxpv3xmhsq
title: Linux logical volume manager
desc: >-
  Title: Linux Logical Volume Manager (LVM) Deep Dive Tutorial
  URL: https://www.youtube.com/watch?v=MeltFN-bXrQ
updated: 1691004754261
created: 1682892837507
---

![LMV basic structure](./assets/Personal/Videos/Linux%20logical%20volume%20manager-%20lmv_basic_structure.png)

## Commands

- `pvcreate /dev/<disk>`: convert the new disk to an LVM physical volume.

- `vgcreate <volgroup name> <physical volume>`: create a volume group.

- `lvcreate <volgroup name>  -L <size> -n <logical volume name>`

- `vgextend <volume group name> <physical volume>`: add the new physical volume to the volume group.

- `lvextend -L +<size> /dev/mapper/<volume group name>-<logical volume name>`: extend the logical volume using the free space in the volume group.

- `resize2fs /dev/mapper/<volume group name>-<logical volume name>`: grow the file system to match the newly available space.

	> You can add the flag `--resize` to the lvextend command to do the 2 things at once.

- `pvdisplay`: displays information about the physical volumes.

- `vgdisplay`: displays information about the volume groups.

- `lvdisplay`: displays information about the logical volumes.
