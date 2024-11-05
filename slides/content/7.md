---
title: "07: memory forensics"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}

# memory forensics
### comp6445 week07

---

### house keeping
![](https://thumbs.gfycat.com/FriendlyWarmLark-max-1mb.gif)
* investigation
* report feedback

---

{{% section %}}

### investigation

|                  |                     |
|------------------|---------------------|
| device last used | 27/07/2021 (check the timeline feature in autopsy) |
| file system used | HFS+ (check the partition table) |
| who owns device  | Joan Sally Smith (bunch of stuff in the user account directory) |
| are you certain  | no (you can never be) |
| fs version       | HFS+ 4 (volume header section contains HFSPlusVolumeHeader) |

---

### harder questions

|                  |              |
|------------------|--------------|
| user's password  | PaSsWoRd (crack the keychain with [johntheripper](https://int0x33.medium.com/day-68-crack-file-key-and-keychain-passwords-with-john-8aeb5df34a54)) |
| hidden passwords | bobbytables (header of /.../Document/agocbaqa0h341) |
|                  | correcthorsebatterystaple (in the file /.../Document/gpj.10mhk4pc3paw0) |
| secrets in keychain | SuperSecret:IShouldBeUsingMFAIn2021 ([chainbreaker](https://github.com/n0fate/chainbreaker) with user's password) |

{{% /section %}}

---

{{% section %}}

## report feedback

|                |          |
|----------------|----------|
| Report AVG     | `74.85%` |
| Reflection AVG | `61.88%` |
| Overall        | `71.11%` |

---

### findings
84%

* Terry editing receipts
* Terry selling customer equipment
* Charlie extorting SWExpert
* Charlie selling secrets to project2400

---

### additional findings
You had to find one of the following

* CCleaner
* Terry's keylogger
* Cygnus hex editor
* Prefetch files for the image editor

---

### style
78%

Just a checklist
* Qualifications of the investigator 
* Declaration 
* Hashes of the files 
* Instructions provided 
* Tools used (with versions) 

---

### explaining the evidence
74%

* If you mention something, explain it
    * e.g. a tool: what is autopsy, what does it do??
    * e.g. a concept: what is a hash, or hex??!?
* A layperson should be able to understand the report (e.g. the jury, a judge, etc)
* Don't make assumptions before you give evidence
* Explain your findings, don't make conclusions until the end

---

### screenshots
72%

* some people didn't include any, which is brave
* if there's something important in the screenshot, highlight it
* include screenshots in the investigation section, not just the appendix
* the images should link to what you're talking about
* if you're attaching images, or files, include their hashes, locations, paths, etc

---

### structure
68%

* separate different "findings" into sections, don't just have everything in one big blob
* label things: number each paragraph/attachment so you can reference them later 
* tables are fantastic & make it really easy to follow
* make my viewing experience pleasurable pls and ty

---

### conclusion
57%

* **reference the specific evidence in your conclusion**
* **actually answer the question from the instructions**
* really important, it shouldn't be 50 words.
* You should be giving your opinion on what you think happened, don't necessarily place blame (unless you can be sure a certain party did it)

---

### reflection part a
68%

* The evidence asked for was generally okay, but the justifications for it were generally a bit weak
* what would you do with the evidence
* how would this evidence strengthen your case?
* be specific!

---

### reflection part b
55%

* the questions should be questioning the integrity of the report, not you as a person
* don't give a soft-ball questions "damn why this report so good", you should be attacking your report, findings holes in it
* reference things discussed in the lectures (only using one tool, lack of evidence)

---

### overall
> the report should be a story

---

### walkthrough
> anyone want to volunteer?

{{% /section %}}

---

## discussion
* any questions about the second report?
* if not, anyone want to play gartic phone?

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
