# How to set up a new hard drive

In theory, mounting a new hard drive to your desktop is fairly straightforward if there's space in your machine. For a computer building noob, there are a few stumbling blocks that I needed to figure out before I can actually mount the drive.

These are the steps I took:

1. Connect your new drive to the motherboard with the SATA cable + power cable
2. run `lsblk` to check that the system can detect the disk (e.g. if it's a second disk it might be listed as `sdb`)
3. make a directory to mount the disk e.g. `sudo mkdir /data`
4. try to mount the disk: `sudo mount /dev/sdb /data`

If 4 works, you are good to go, otherwise, you might need to partition the disk first. (e.g. when I tried the above I got `mount: /data: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.`)

I thought I could fix it with [fsck](https://en.wikipedia.org/wiki/Fsck), but no luck

```
sudo fsck /dev/sdb
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

Finally, on reading https://techguides.yt/guides/how-to-partition-format-and-auto-mount-disk-on-ubuntu-20-04/, I realised I need to partition the disk first, so:

5. Run `sudo gdisk /dev/sdb`
6. enter `n` (for new partition)
7. enter 1 (for 1 new partition, you can use another number if you want)
8. press enter on the next few questions to accept the defaults
9. enter `w` to write the settings to disk

10. Finally, mount the drive with the command at 4.

11. you can also change disk settings e.g. automount on startup using `sudo gnome-disks`

```
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): ?
b	back up GPT data to a file
c	change a partition's name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-3907029134, default = 2048) or {+-}size{KMGTP}:
Last sector (2048-3907029134, default = 3907029134) or {+-}size{KMGTP}:
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300):
Changed type of partition to 'Linux filesystem'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.
(base)  wwymak@wwymak-dl-box  ~  sudo mkfs.ext4 /dev/sdb
mke2fs 1.44.1 (24-Mar-2018)
Found a gpt partition table in /dev/sdb
Proceed anyway? (y/N) y

```
