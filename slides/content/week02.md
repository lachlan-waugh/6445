---
title: "week02: forensic method"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}
# 6445 Week02
### the forensic process

---

{{% section %}}

## Lecture content

---

## The forensic process
* Digital evidence must be collected via a standard, documented, and proven forensic process

---

## Forensically sound
> Which two aspects are required for evidence to be admissible?

---

## Forensically sound
* Two aspects for evidence to be admissible?
    * **defensible**: accepted as industry standard and/or proven to be sound
    * **repeatable**: well-documented, 3rd party could replicate it with the same results. 

---

## Drive structure
* **file system**: data structure for organisation of files 
* **volume**: container for a file system
* **sector**: smallest storage unit of a drive (512B) 
* **clusters**: groups of sectors
* **unpartitioned space**: .

> harddrive: [meme](https://www.youtube.com/watch?v=JcJSW7Rprio)

---

## Hidden items
> Where could you look for hidden information on a drive?

---

## Hidden items
* Where to look for hidden information on a drive?
    * Hidden partitions (e.g. modified PT)
    * Unallocated space
    * Slack (drive and volume)
 
---

## Additional areas
* Host Protected Area
* Device Configuration Overlay

> Read more [here](https://superuser.com/a/1515612)

---

## SDD vs HDD
> Would it be harder to carve files on a HDD or SDD, why?

{{% /section %}}

---

## Reports
* I would suggest that you start now
* Keep a note of your process
* I'll release a template report next week

---

## Random extra stuff
> I found this wierd file on my computer, you can download it [here](https://drive.google.com/file/d/1PNkpe8OY9TZa4-NcHOhrztf-OD6MSpk_/view?usp=drive_link)

---

## Walkthrough
> Was there any challenges last week you couldn't solve?

---

## Challenges
