TryHackMe — Presecurity

**Series:** TryHackMe Room Walkthroughs · Room 01 **Platform:** [TryHackMe](https://tryhackme.com/) **Module:** Presecurity (introductory) **Focus:** Offensive vs. defensive security, hands-on reconnaissance and triage, and the cybersecurity career landscape **Companion article:** \[Hashnode : add link after publishing\]

> **Series note:** This is Room 01 of an ongoing TryHackMe Room Walkthroughs series. Each entry documents method and understanding, not flags or quiz answers, so the rooms keep their learning value for other beginners.

---

## Objective

Get a working, hands-on introduction to both sides of security attacking (offensive) and defending (defensive) and build a realistic picture of the careers, roles, and entry paths in the field.

Three lessons, each with a distinct focus:

1. **Offensive security** — simulate an attacker to find weaknesses.
2. **Defensive security** — investigate and stop attackers to protect an organisation.
3. **Careers in cybersecurity** — what the field is, who it needs, and where a beginner fits.

---

## Scope & Ethics

This report documents **method and understanding**, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This is a study artifact, not a solution key.

All testing was performed inside TryHackMe's sandboxed environment against intentionally vulnerable targets. No real systems were touched.

---

## Environment

- Platform: TryHackMe (web-based virtual environment)
- Room type: Foundational guided exercises against a simulated target and a simulated security dashboard
- Tools used: `dirb` (DirBuster-style web content discovery) a browser and TryHackMe's in-room security dashboard simulator

---

## Lesson 1 Offensive Security

### Concept

Offensive security is the practice of simulating a hacker's actions to find weaknesses before an adversary does. The goal is to think like an attacker so you can find the gaps first.

### What I did

1. Defined offensive security in my own words.
2. Visited a simulated online banking application to find a valid account on the app.
3. Used `dirb` to discover hidden pages on the target:

```bash
dirb http://fakebank.thm
```

4. Used an account discovered through the hidden page to deposit funds demonstrating how an exposed or unlinked page can be abused.

### What I learned

- Web content discovery tools like `dirb` look for paths a site doesn't advertise hidden directories and pages are a common real-world weakness.
- A page being "not linked" is not the same as "not reachable." If it's served, it can be found.
- **Defender takeaway:** inventory and access control matter. Unlinked admin pages, debug endpoints and forgotten directories are exactly what an attacker enumerates first.

---

## Lesson 2 Defensive Security

### Concept

Defensive security is the work of investigating and stopping attackers to protect a company, website, or system. Where offensive security asks "how would someone get in?" defensive security asks "is someone in, and how do I stop them?"

### What I did

1. Defined the role of a defender.
2. Reviewed recent alerts on a simulated security dashboard and identified the most suspicious one an active attack in progress and noted the source IP address.
3. Used the dashboard's **Investigate** function to review the pages the attacker had tried to visit, and identified the most recent page reached: the admin page of a banking application.
4. Blocked the attacker's connection and IP address, slowed the activity, and turned on protection.

### What I learned

- A defender's first move on an alert is **triage**: which alert looks most suspicious, and why?
- Following an attacker's path through the pages they touched tells you *what they were after* — here, the admin page of a banking app.
- Containment (blocking the IP, slowing activity, enabling protection) is the practical response once you've confirmed the threat.
- **Defender takeaway:** alert review, investigation, and containment are the core loop of SOC work. This lesson was my first hands-on taste of that loop.

---

## Lesson 3 Careers in Cybersecurity

### Concept

Cybersecurity is a broad, fast-growing field that is short on people and open to a wide range of backgrounds. It is not a single job.

### What the field looks like

- **Many roles, not one.** The field spans more than 50 recognised roles penetration testers, SOC analysts, threat intelligence researchers, incident responders, security engineers, and more. Different roles suit different ways of thinking: some think like attackers, some like detectives, some like researchers tracking how threats evolve.
- **Background is not a barrier.** People enter from policing, healthcare, finance, teaching, and many other fields. The skills that make people effective curiosity, calm under pressure, problem-solving are not exclusive to computer science graduates.
- **Entry is more accessible than it looks.** Competitive entry-level pay, senior roles that pay well, and a path that doesn't require a decade of formal education. Certifications and hands-on practice can move someone from no experience to a paying role faster than many other professions.
- **The work matters.** When defences fail, the consequences are real: hospitals cancel appointments, banks freeze, power grids go down, factories stop, and stolen personal data causes harm for years. The people who stop those incidents aren't lucky they're prepared.
- **The field keeps growing.** New technology AI, cloud, connected healthcare, digital banking creates new roles and new things to protect.

### What I learned

- I don't have to pick "cybersecurity" as one job; I can aim at a role that fits how I think. For me, that's the defensive side SOC analysis and incident response.
- My computer science background is an advantage, not a requirement the field explicitly values diverse backgrounds and non-technical strengths.
- The fastest way in is practice plus proof of work, which is exactly why I'm documenting this journey publicly.

---

## Key Takeaways

| Concept | Meaning |
| --- | --- |
| Offensive security | Simulating an attacker to find weaknesses first. |
| Defensive security | Investigating and stopping attackers to protect an organisation. |
| Content discovery | Tools like `dirb` find unlinked pages "not linked" ≠ "not reachable." |
| Alert triage | Identifying the most suspicious alert and why. |
| Attack path reconstruction | Following the pages an attacker touched to understand intent. |
| Containment | Blocking the source, slowing activity, enabling protection. |
| Career breadth | 50+ roles; different thinking styles fit different roles. |
| Entry paths | Background-agnostic, practice-driven, certification-supported. |

---

## Lessons Learned

- Offence and defence are two lenses on the same system, understanding both makes you better at either.
- Hidden web content is a real and common weakness, inventory and access control are the defence.
- SOC work is a loop: triage → investigate → contain. This room gave me my first hands-on run through it.
- The field is broad and open; the practical path in is hands-on practice plus visible proof of work.

---

## Next Steps

- Continue the TryHackMe Room Walkthroughs series (next room: Computer Fundamentals).
- Go deeper on web content discovery: wordlists, status-code filtering, and why unlinked endpoints exist.
- Study SOC alert triage workflows and the tools that support them.

---

*Part of the TryHackMe Room Walkthroughs series. Companion article on Hashnode (link to be added after publishing).*

*Until then, keep exploring, keep experimenting, keep learning.*
