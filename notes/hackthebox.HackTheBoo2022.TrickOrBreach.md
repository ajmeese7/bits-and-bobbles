---
id: t5n4reog2hnkgli8rf91tkt
title: Trick Or Breach
desc: ''
updated: 1666539454411
created: 1666535065811
tags:
  - hackthebox
  - easy
  - dns
  - exfiltration
  - forensics
---

```shell
# Extract the DNS query data from the pcap;
# https://unix.stackexchange.com/a/393503/370076
tshark -r ./capture.pcap -T fields -e dns.qry.name -Y 'dns.flags.response == 0' > raw_exfil.txt

# Get only the data from the DNS queries;
# https://www.hackucf.org/hack-all-the-things/hack-all-the-things-exfiltrating-data-via-dns-requests
egrep -o "[0-9a-f]+.pumpkincorp.com" ./raw_exfil.txt | cut -d. -f1 > exfil.txt

# Unhex the exfiltrated data
xxd -r -p < exfil.txt > data
```

Looking at the `data` file, I determined that it was an archive that was really an Excel spreadsheet. I opened it in OpenOffice and found the flag:

```text
HTB{M4g1c_c4nn0t_pr3v3nt_d4t4_br34ch}
```
