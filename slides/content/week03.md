---
title: "week03: filesystems"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}
# file systems
### comp6445 week03

---

## File systems
* FAT32
* NTFS
* Ext

---

### FAT32
{{% section %}}
* File Allocation Table (FAT)
* Directory Entries (DE)

---

![](/assets/img/week03/fat32.png)

---

> FAT: linked list of statuses of all clusters

| status       | indicates                                       |
| ------------ | ----------------------------------------------- |
| `0x?0000000` | free cluster                                    |
| `0x?0000002` | cluster in use (value is next cluster for file) |
| `0x?FFFFFFF` | cluster in use EOF marker                       |

---

### Deleted files
* what happens to file contents when a file is deleted
* what else happens (specifically in FAT?)

---

### Deleted files
* what else happens (specifically in FAT?)
    * first character in filename changed to `0xe5`
    * all clusters in FAT replaced with `0x00`

> why are these important

{{% /section %}}

---

### NTFS
{{% section %}}
* $MFT (DEs of NTFS)
* $BITMAP (FATs of NTFS)

* Everything is a file™
* Everything in a file is an attribute 

---

![](/assets/img/week03/ntfs.png)

---

### Extents
* Similar to Cluster Runs
* A contiguous area of storage reserved for a file

---

### Alternative data streams
* Also a file attribute
* Honestly pretty stupid, not honored by other FSs
    * Originally used to provide compatibility with Macs
    * Now mostly used to hide malware lol

> read more [here](https://owasp.org/www-community/attacks/Windows_alternate_data_stream)

---


### Deleted files
* what happens for NTFS

{{% /section %}}

---

### Deleted files
* what happens for NTFS
    * `$MFT` marks `$FILE` entry as available
    * `$DATA` attribute read, `$BITMAP` updated to show cluster runs no longer used
    * nothing is wiped/deleted from `$MFT` or clusters

> until the FILE entry is overwritten, the data is still there

---

### Ext
{{% section %}}

{{% /section %}}

---

## Random extra stuff
> I found another wierd file on my computer, you can download it [here](/6445/demos/anotherone/whatisthis)

---

## Investigation
> Any questions so far?

---

## Walkthrough
> Any questions about last week's investigation
