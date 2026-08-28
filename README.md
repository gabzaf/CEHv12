# CEH v12 study notes

Personal notes from studying for **Certified Ethical Hacker (CEH) v12**, started in September 2024 as red-team / ethical-hacking study.

This is not a course, a lab, or a complete exam dump. It is a linear notebook: concepts rewritten in first person while studying, with a few Portuguese asides. Commits are almost all titled `studying` / `Estudando` because the repo was used as a daily study log.

Work stopped in October 2024, partway through footprinting. Later CEH modules (scanning, enumeration, system hacking, malware, sniffing, social engineering, web, wireless, cloud, crypto, and so on) were never started here.

## How to read this repo

Read the chapters in order. Each file is one study session stream, not a polished summary.

```
chapter_1  →  what ethical hacking is, and the attack models
chapter_2  →  networking you need before you can talk about attacks
chapter_3  →  CIA, risk, policy, and defensive technology
chapter_4  →  first offensive phase: recon / OSINT  (unfinished)
```

Every file starts with a `#Topics covered:` line. Use that as the table of contents for that chapter.

| Chapter | File | What you studied | Completeness |
| --- | --- | --- | --- |
| 1 | [`chapter_1/ethical_hacker.txt`](chapter_1/ethical_hacker.txt) | Ethics, engagement scope, attacker models, five phases of a test | Finished |
| 2 | [`chapter_2/network_foundations.txt`](chapter_2/network_foundations.txt) | OSI / TCP/IP, topologies, Ethernet, IP, subnets, TCP/UDP/ICMP, isolation, VPNs | Mostly done; a few headings are empty |
| 3 | [`chapter_3/security_foundations.txt`](chapter_3/security_foundations.txt) | CIA / Parkerian Hexad, risk, policies, ATT&CK, firewalls, IDS/IPS, EDR, SIEM, logging | Longest and most complete |
| 4 | [`chapter_4/footprinting_and_reconnaissance.txt`](chapter_4/footprinting_and_reconnaissance.txt) | OSINT, EDGAR, whois / RIRs, people harvesting | Started only; later headings are empty |

## Chapter 1 — The ethical hacker

Covers why the work exists, the code of conduct (confidentiality, disclosure, written scope), and how testers are supposed to think like an attacker without becoming one.

Attack models compared in the notes:

- **Cyber kill chain** — recon → weaponization → delivery → exploitation → installation → C2 → actions on objectives
- **Attack lifecycle** — recon, initial compromise, foothold, privilege escalation, then a loop of internal recon / lateral movement / persistence, then complete mission
- **MITRE ATT&CK** — taxonomy of real-world TTPs (tactics, techniques, procedures), not a linear checklist

Then the classic five-phase ethical-hacking methodology:

1. Reconnaissance and footprinting
2. Scanning and enumeration
3. Gaining access
4. Maintaining access (persistence)
5. Covering tracks

Chapter 4 is the start of phase 1. Phases 2–5 were never written up in this repo.

## Chapter 2 — Network foundations

Networking background needed to understand later CEH topics: how traffic is addressed, forwarded, and isolated.

Main blocks:

- **Communications models** — protocol as a convention; OSI seven layers vs TCP/IP as an as-built architecture
- **Topologies** — bus, star, ring, mesh, hybrid (star-bus)
- **Physical / layer 2** — Ethernet frames, MAC addresses (OUI + device), broadcast `ff:ff:ff:ff:ff:ff`, switching / CAM tables
- **IP** — IPv4 (loopback, RFC1918 private ranges, multicast), IPv6 unicast/anycast/multicast, subnet masks and CIDR, network vs broadcast addresses
- **Transport** — TCP (ports, three-way handshake, reliable delivery); UDP heading is empty
- **ICMP** — type/code, ping, traceroute
- **Architecture** — LAN / VLAN / WAN / MAN, DMZ, enclaves (PCI, PHI), microsegmentation
- **Remote access** — MPLS, IPsec, TLS VPNs
- **Cloud computing** — heading only, never filled in

Empty or stub sections inside the file: `Headers`, `Octets vs Bytes`, TCP header field notes, `UDP`, `Cloud Computing`.

## Chapter 3 — Security foundations

The largest file. Moves from “what security is” to “how organizations actually try to implement it.”

1. **CIA triad** — confidentiality (at rest / in transit), integrity, availability; Parkerian Hexad extras (possession, authenticity, utility)
2. **Risk** — `risk = probability × loss`; threat, vulnerability, exploit, threat actor, threat vector; controls that are preventive / detective / corrective and technical / administrative / physical
3. **Risk treatment** — accept, transfer, mitigate, avoid
4. **Governance stack** — policy (intent) → standards (how the policy is implemented) → procedures (step-by-step) → optional guidelines
5. **ATT&CK again**, this time as a way to design detections, not only to describe attackers (APT vs smash-and-grab)
6. **Security technology**, walked up the stack:
   - firewalls: packet filter → stateful → DPI → application-layer (WAF, SBC) → UTM
   - IDS vs IPS (Snort-style rules, placement, false positives)
   - EDR (remote artifacts, host isolation)
   - SIEM / SOC (correlation; Elastic Stack mentioned)
7. **How to think about architecture** — defense in depth, defense in breadth, defensible network (choke points, segmentation)
8. **Evidence** — syslog vs Windows Event Log, Linux `auditd` / `auditctl`, why remote logging matters

There is one Portuguese note in the integrity section explaining what an HTTP session actually is.

## Chapter 4 — Footprinting and reconnaissance

First offensive-side chapter, and the last one started.

Written so far:

- Why footprinting exists (size the attack surface without tipping off the target)
- Open-source intelligence (OSINT) vs illegal / physical collection
- Company research: EDGAR (SEC filings), domain registrars, ICANN / IANA, RIRs and `whois`
- People: `theHarvester` as an example of gathering contacts from public search

Headings that exist but have no notes:

- Domain Name System
- Passive Reconnaissance
- Website Intelligence
- Technology Intelligence

Port scanning, vulnerability scanning, and the rest of “technical assessment methods” from the chapter header were never reached.

## Suggested path if you pick this up again

1. Skim chapter 1 if you only need the models (kill chain vs lifecycle vs ATT&CK vs the five phases).
2. Use chapter 2 as a networking cheat sheet (especially subnets/CIDR, MAC vs IP, TCP handshake, DMZ/enclaves).
3. Use chapter 3 as the defensive map (CIA, risk language, firewall types, IDS/IPS/EDR/SIEM).
4. Treat chapter 4 as a stub: finish DNS, passive recon, and website/tech intel before moving on to scanning.

If the goal is still CEH, the missing material after chapter 4 is most of the exam outline.

## What this repo is not

These notes describe concepts from study material. They are not a playbook, a lab, or instructions for attacking systems. Anything that looks like a command or rule snippet (iptables, Snort, ModSecurity, `theHarvester`) is there as an illustration of how a control or recon source works, copied while studying.
