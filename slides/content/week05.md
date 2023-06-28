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

### how did you find the report
> any comments?

---

{{% section %}}

### memory forensics

---

### what is it?
* investigating a dump of the RAM from a computer system

---

### when is this useful
> when?

---

### when is this useful
* there's a lot you can't get from a harddisk image
    * if/when a program was executed
    * how it was executed (arguments, lifespan)

* some malware never touches the disk

---

### fileless malware
* even if it never touches disk, at some point, it has to be in memory
* process hollowing: when a legitimate process is paused, duplicated, and then it's executable memory is replaced with malicious code
* this can bypass simple AVs which ignore whitelisted/trusted services

> read more [here](https://www.trellix.com/en-au/security-awareness/ransomware/what-is-fileless-malware.html) and [here](https://www.crowdstrike.com/cybersecurity-101/malware/fileless-malware/)

---

![](/assets/img/week05/inmemory-malware.png)

---

### what could you find in memory?
> what

---

### what could you find in memory?
* recently executed commands
* running processes, and their code/DLLs
* drivers & daemons
* passwords, security keys, security information

{{% /section %}}

---

{{% section %}}

### collecting memory dumps
* RAM is volatile, you can't capture it after the computer is shutdown 
* It can be hard to collect when it's live (you don't want to change the machines state)

---

### when could collecting memory be difficult?
* if the data is stored in a datacenter/cloud provider
    * how would you collect it?

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
* `windows.pstree`
    * get processes tree (not hidden)
* `windows.pslist`
    * get process list (EPROCESS)
* `windows.psscan`
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
* `windows.cmdline`
    * shows the arguments used for the process
* `windows.envars [--pid <pid>]`
    * display process environment variables
* `windows.handles --pid <pid>`
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
* `windows.strings --strings-file ./strings_file`
    * TODO 
* `windows.vadyarascan --yara-rules "https://" --pid <PIDS>`
    * TODO
* `yarascan.YaraScan --yara-rules <R>`
    * TODO

---

### dumping hashes
* `windows.hashdump`
    * grab common windows hashes (SAM+SYSTEM)
* `windows.cachedump`
    * grab domain cache hashes inside the registry
* `windows.lsadump`
    * grab lsa secrets

---

### reference list
* command list can be found [here](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference)
* some other [stuff](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet)

{{% /section %}}

---

## Demo
another stolen [challenge](https://mega.nz/#!sh8wmCIL!b4tpech4wzc3QQ6YgQ2uZnOmctRZ2duQxDqxbkWYipQ)

> can you find Rick's password?

---

## Tutorial
> finally, another investigation
