---
title: "Week04"
layout: "bundle"
outputs: ["Reveal"]
---

## We'll get started at 19:05

---

{{< slide class="center" >}}
# network forensics
### comp6445 week04

---

{{% section %}}

## Network forensics

---

### What is a packet?
* a chunk of data, forming part of a complete message

* max packet size is about 65kb, so what happens when you stream a movie 

---

### What is in a packet

* All packets contain a header and a payload

* Payload is all the data

* Header contains any metadata (e.g. length, protocol, source, destination)

---

### OSI What
![](/assets/img/week04/osi_model.jpg)

---

### What is a packet capture?
* Intercepting packets travelling across a network, and logging them to a file

> What could be a problem with this?

---

### Demo

{{% /section %}}

---

{{% section %}}

### wireshark
> how to use it

---

### filters
* there's two types of filters
    * display filters: match metadata about the packet (e.g. source ip, protocol) 
    * pattern matching: match content in the filter (e.g. packet bytes/details)

---

### display filters
* just a boolean expression (similar to C)
    * `(f_1 eq AAA && f_2 ne BBB) || f_3`
* you can search by
    * **protocol** (e.g. `http`) 
    * **ip** (e.g. `ip.src_host` and `ip.dst_host`)
    * and a bunch more [here](https://wiki.wireshark.org/DisplayFilters) and [here](https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html)

---

### following conversation
each packet will be tied to a "conversation"
* you can follow them by
    * right clicking a packet > `follow X stream`
    * filtering for `X.stream eq N`

> `X` would be `TCP` or `UDP`

> `N` would be a number

---

### what should I be looking for
* wierd IPs being communicated with
* files being downloaded/uploaded
* you can look for communicaion made at the same as evidence you found

---

### decrypting traffic
Some traffic will be encrypted (e.g. SSH/HTTPS), so you won't be able to read the packets
* Edit > Preferences
* Protocols > TLS

> There you can you upload the tls/ssl keys to decrypt the traffic

{{% /section %}}

---

{{% section %}}

## Report writing

---

### What not to do
* Be overly verbose

* Make stuff up (I did the same investigation)

* Speak outside of your competence

* Make a decision too hastily

---

### Review

> Bad report

---

### What to do

* Document the process

* Explain why you did certain things

* Explain what the evidence means

* Align the evidence

---

### Review

> My report (also bad)

{{% /section %}}

---

## Questions?

---

## Investigation
