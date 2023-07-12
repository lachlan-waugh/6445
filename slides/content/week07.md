---
title: "Week07"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}
# report feedback
### comp6445 Week07

---

### house cleaning
![](https://thumbs.gfycat.com/FriendlyWarmLark-max-1mb.gif)
* reflections
* investigation
* reports

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

### Mindset
* a lot of people seem to be struggling with this
* don't just blindly investigate the image
* google to find where interesting things could be
* use your intuition for where you might find things (e.g. Documents/Downloads/Recycling Bin)

---

{{% section %}}

### reflections
avg: `75%`

* quite a few people haven't been doing these
* literally just do them?
* if write a reasonable amount you'll get the marks
* it takes no time and it's worth 10% overall

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

## demo
> investigation #4
