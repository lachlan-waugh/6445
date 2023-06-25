---
title: "Week05"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}

# memory forensics
### comp6445 week05

---

{{% section %}}

### memory forensics


---

### collecting memory dumps
* RAM is volatile, you can't capture it after the computer is shutdown 

{{% /section %}}

---

### what processes are sus ඞ
{{% fragment %}}
obfuscate names/paths (drop some malware in a system location and give it a legitimate name)
{{% /fragment %}}
{{% fragment %}}
misspelled versions of proper system processes
{{% /fragment %}}
{{% fragment %}}
proper system names in wrong location
{{% /fragment %}}
{{% fragment %}}
duplicate processes that should only spawn once
{{% /fragment %}}
{{% fragment %}}
processes that have a parent they shouldn’t
{{% /fragment %}}
{{% fragment %}}
system processes with start time much later in life
{{% /fragment %}}
{{% fragment %}}
system processes running under a user account
{{% /fragment %}}

---

{{% section %}}

### volatility
> cause RAM is volatile lol

---

### list all the processes
* `windows.pstree.PsTree`
    * get processes tree (not hidden)
* `windows.pslist.PsList`
    * get process list (EPROCESS)
* `windows.psscan.PsScan`
    * get hidden process list (e.g. malware)

---

### dumping a process
* `windows.dumpfiles --pid <PID>`
    * get the executable & DLLs
* `windows.memmap --dump --pid <PID>`
    * get all memory resident pages
* `windows.dllist --pid <PID>`
    * list the DLLs used by a process

---

### see how a process was started
* `windows.cmdline.CmdLine`
    * shows the arguments used for the process
* `windows.envars.Envars [--pid <pid>]`
    * display process environment variables
* `windows.handles.Handles --pid <pid>`
    * show files, threads, etc a process has opened

---

### registries
* `windows.registry.hivescan`
    * TODO
* `windows.registry.hivelist`
    * TODO
* `windows.registry.printkey -K "Path\To\Key"`
    * TODO 

---

### viewing files
* `windows.filescan`
    * TODO
* `windows.dumpfiles`
    * TODO
* `windows.dumpfiles --virtaddr <o>`
    * TODO
* `windows.dumpfiles --physaddr <o>`
    * TODO

---

### networking
* `windows.netscan`
    * TODO
* `windows.netstat`
    * TODO 

---

### pattern match strings
* `windows.strings.Strings --strings-file ./strings_file`
    * TODO 
* `windows.vadyarascan.VadYaraScan --yara-rules "https://" --pid <PIDS>`
    * TODO
* `yarascan.YaraScan --yara-rules <R>`
    * TODO

---

### dumping hashes
* `windows.hashdump.Hashdump`
    * grab common windows hashes (SAM+SYSTEM)
* `windows.cachedump.Cachedump`
    * grab domain cache hashes inside the registry
* `windows.lsadump.Lsadump`
    * grab lsa secrets

---

* command list can be found [here](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference)
* some other [stuff](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet)

{{% /section %}}

---

## Demo

---

## Tutorial

---

## Walkthrough
