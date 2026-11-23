# TryHackMe : SOC Fundamentals

**Series:** TryHackMe Room Walkthroughs · Room 04
**Platform:** [TryHackMe](https://tryhackme.com/)
**Module:** SOC Fundamentals
**Focus:** The pillars of a Security Operations Center (People, Process, Technology) and practical alert triage.
**Companion article:** (https://darajat.hashnode.dev/soc-fundamentals)

> **Series note:** This is Room 04 of an ongoing TryHackMe Room Walkthroughs series. Each entry documents method and understanding, not flags or quiz answers, so the rooms keep their learning value for other beginners.

---

## Objective

Build a baseline understanding of a Security Operations Center (SOC), including its core components, the roles within the team, the processes used for detection and response, and the technology that supports them. 

---

## Scope & Ethics

This report documents method and understanding, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This is a study artifact, not a solution key.

---

## Environment

- Platform: TryHackMe, browser-based virtual environment
- Room type: Foundational SOC theory and practical alert triage
- Prerequisite knowledge assumed: None, beginner-friendly

---

## Lesson 1 : Introduction to SOC

**Core idea:** Traditional security is no longer enough. Organizations need a dedicated team watching the network 24/7.

As technology becomes more efficient, the responsibility to protect it grows. Threat actors are constantly finding new vulnerabilities to exploit. A SOC (Security Operations Center) is a dedicated facility operated by a specialized team. Their mission is continuous monitoring to identify suspicious activity and prevent damage before it happens.

---

## Lesson 2 : Purpose and Components of SOC

**Core idea:** The SOC's main focus is Detection and Response.

The SOC uses centralized security solutions to monitor the entire company network. This breaks down into two main components:

**1. Detection**
- **Vulnerabilities:** Identifying weaknesses in software or systems that attackers could exploit.
- **Unauthorized Activity:** Spotting attackers who have compromised credentials and are logging in from unusual locations.
- **Policy Violations:** Catching employees breaking rules (e.g., downloading pirated media or sending confidential files insecurely).
- **Intrusions:** Detecting unauthorized access, such as a successful web application exploit or a user infecting their computer via a malicious site.

**2. Response**
Once an incident is detected, the SOC supports the incident response team by minimizing the impact and performing root cause analysis.

To be effective, a SOC relies on three pillars: **People, Process, and Technology**. All three must coexist to mature the environment.

---

## Lesson 3 : People (The First Pillar)

**Core idea:** Technology is useless without human intervention.

Security solutions generate massive amounts of "noise" (false positives). Humans are needed to identify truly harmful activities. The SOC team is structured to handle this:

- **SOC Analyst (Level 1):** The first responders. They perform basic alert triage to determine if a detection is harmful and escalate as needed.
- **SOC Analyst (Level 2):** Dives deeper into investigations, correlating data from multiple sources for proper analysis.
- **SOC Analyst (Level 3):** Experienced professionals who proactively hunt for threats and lead detailed incident responses (containment, eradication, recovery).
- **Security Engineer:** Deploys and configures the security solutions to ensure smooth operation.
- **Detection Engineer:** Creates the logic (security rules) behind the security solutions to detect harmful activities.
- **SOC Manager:** Manages the processes, supports the team, and reports the security posture to the CISO.

*(Note: Team sizes and roles vary based on organizational needs).*

---

## Lesson 4 : Process (The Second Pillar)

**Core idea:** Every role follows specific processes, with Alert Triage being the foundation.

- **Alert Triage:** The first response to any alert. It determines the severity and helps prioritize. The goal is to answer the **5 Ws**:
  - **Who:** Who is involved? (e.g., User George)
  - **What:** What happened? (e.g., Malware detected)
  - **Where:** Where did it happen? (e.g., Host: GEORGE PC)
  - **When:** When did it happen? (e.g., 13:20 on June 5)
  - **Why:** Why did it happen? (e.g., The user downloaded pirated software)

- **Reporting:** Escalating harmful alerts as tickets to higher-level analysts with thorough analysis and evidence.
- **Incident Response & Forensics:** High-level teams initiate deeper investigations to determine the root cause using system artifacts.

---

## Lesson 5 : Technology (The Third Pillar)

**Core idea:** Security solutions centralize data and automate detection to minimize manual effort.

- **SIEM (Security Information and Event Management):** Collects logs from various network devices, correlates them using detection rules, and alerts on suspicious matches. *(Note: SIEM only provides detection, not response).*
- **EDR (Endpoint Detection and Response):** Provides real-time and historical visibility of device activities at the endpoint level, allowing for automated responses.
- **Firewall:** Acts as a barrier between internal and external networks. Monitors traffic and blocks suspicious traffic before it reaches the internal network.
- **Other Solutions:** Antivirus, EPP, IDS/IPS, XDR, SOAR.

---

## Lesson 6 : Practical Exercise

**Core idea:** Applying the 5 Ws to a real-world alert.

**Scenario:** As a Level 1 SOC Analyst, I received an alert for port scanning activity on a host. The vulnerability assessment team noted they were running the scan internally.

**Execution:**
Using the SIEM solution, I investigated the associated logs and answered the 5 Ws. I determined the activity that triggered the alert, the reason for the scan, and verified if any response was sent back to the scanner.

**Why it matters:** This practical exercise simulated the daily life of a Level 1 Analyst. It tested critical thinking and analytical skills by forcing me to interpret raw logs to understand the full context of an alert.

---

## Key Takeaways

| Concept | Meaning |
| --- | --- |
| SOC Purpose | Continuous monitoring and response to protect the organization. |
| Detection & Response | The two primary components of SOC operations. |
| The 3 Pillars | People, Process, and Technology must work together. |
| Alert Triage (5 Ws) | Who, What, Where, When, Why. The basis of initial alert analysis. |
| SIEM | Correlates logs from multiple sources to detect threats. |
| EDR | Monitors and responds to endpoint-level activity. |

---

## Lessons Learned

- The SOC is not just about tools; it is a structured environment where human analysts make sense of automated alerts.
- Alert Triage is a critical skill. Answering the 5 Ws provides immediate context and severity.
- Understanding the different SOC roles (L1, L2, L3) clarifies the career progression path for aspiring analysts.
- Technology (SIEM, EDR, Firewall) is the backbone of the SOC, but it requires skilled People and robust Processes to function.

---

## Next Steps

- Continue the TryHackMe Room Walkthroughs series. Next room to be confirmed.
- Practice answering the 5 Ws on simulated network alerts.
- Explore how SIEM queries are written (e.g., Splunk, Elastic).

---

*Part of the TryHackMe Room Walkthroughs series. Companion article on Hashnode, link: (https://darajat.hashnode.dev/soc-fundamentals)*

*Until then, keep exploring, keep experimenting, and keep learning.*
