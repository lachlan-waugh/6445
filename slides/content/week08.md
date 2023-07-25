---
title: "08: mobile forensics"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}
# mobile forensics
### comp6445 week08

---

### report reflection
* what did you think about them? waht could be improved
* how do you feel you went? did you improve?
---

{{% section %}}

### investigation

|                |                     |
|----------------|---------------------|
| memory profile | WinXPSP2x86 (woops vol3 doesn't use these) |
| nt hash        | 31d6cfe0d16ae931b73c59d7e0c089c0 |
| password       |  |
| antivirus      | no |
| keylogger pid  | 2360 (I showed this) |

---

### investigation p2

|                      |              |
|----------------------|--------------|
| keylogger installed? | can't tell |
| keylogger running?   | no |
| remote access?       | 5800;5900 |
| memory sample?       | mdd\_1.3.exe |

{{% /section %}}

---

## mobile forensics
{{% section %}}

### types of extraction
* logical extraction
* physical extraction

> what's the difference?

---

### what might you gather from a phone?
> what are some pieces of information you can get from a phone, but not a harddrive?

---

### what are the difficulties of getting data from phones

---

### what are the difficulties of getting data from phones
* multiple types of phones (consistency)
* passwords/encryption
* remote wipes
* changing state: receiving messages/calling devices, device syncing with cloud
* difficulty to completely power down device

---

### what are some methods you could use to seize a device?

---

### how has mobile forensics evolved over time?

{{% /section %}}
