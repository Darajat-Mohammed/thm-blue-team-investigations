# TryHackMe — Computer Fundamentals

**Platform:** [TryHackMe](https://tryhackme.com/)
**Module:** Computer Fundamentals
**Focus:** Hardware, system components, and the boot process — viewed from a defender's perspective
**Companion article:** [Hashnode article link — add after publishing]

---

## Objective

Build a working model of what a computer is made of, how the parts connect, and what happens between pressing the power button and the operating system taking over — with a security lens applied to each stage.

Three guiding questions were used throughout:

1. What are the parts?
2. How are they connected?
3. Who or what can reach each part, and how?

---

## Scope & Ethics

This report documents **method and understanding**, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This report is a study artifact, not a solution key.

---

## Environment

- Platform: TryHackMe (web-based virtual environment)
- Room type: Foundational / no live target
- Prerequisite knowledge assumed: none (beginner-friendly)

---

## Lesson 1 — Understanding What I'm Securing

**Core idea:** You cannot defend what you do not understand.

The room frames a computer as a castle. Before a guard can protect it, they need the floor plan: where the treasure is, where supplies are stored, who may enter which room, and how anyone gets in. A guard who has never seen the castle cannot guard it.

**Defender takeaway:** Security work begins with inventory and architecture — the floor plan comes before the lock.

---

## Lesson 2 — The Building Blocks Inside a Computer

Every computer, from laptop to server, is assembled from the same class of parts. Each part has a job, and the system only functions when all of them do theirs.

### Component reference

| Part | Function | Defender relevance |
| --- | --- | --- |
| Motherboard | Main circuit board; everything connects through it. Firmware lives on it. | Central path for all component traffic; firmware is an early-code attack surface. |
| CPU | Executes instructions; modern CPUs have multiple cores. | All software — legitimate or malicious — becomes CPU instructions. |
| RAM | Volatile working memory for whatever the CPU is actively using. | Can hold passwords/keys in use; volatile, so memory capture precedes shutdown in investigations. |
| SSD / HDD | Persistent storage (HDD = moving parts, cheaper per GB; SSD = no moving parts, faster). | Where data persists; lost/stolen drives are why disk encryption matters. |
| Network adapter | Connects the machine to others (wired or Wi-Fi). | The machine's network doorway; ties into networking fundamentals. |
| Power supply (PSU) | Converts wall power and distributes it to components. | Failure = availability loss. |
| Graphics card | Renders output; excels at parallel computation. | GPU parallelism is why password-cracking tools leverage GPUs. |
| Input/output devices | Keyboards, mice, microphones in; monitors, printers, speakers out (USB, HDMI, DisplayPort). | Every port is an entry point; a plugged-in USB device is a classic attack vector. |

### RAM vs. storage — the desk and the filing cabinet

- **RAM = desk.** Small, instantly accessible, cleared at end of day (volatile).
- **Storage = filing cabinet.** Large, persistent across power loss.

Programs and open files are loaded from storage into RAM while in use. When power is lost, the desk is wiped; the cabinet remains. RAM generations (DDR4, DDR5) differ in speed.

### Storage types

- **HDD:** spinning platter with a moving arm — like a record player.
- **SSD:** no moving parts — like a large USB stick; far faster.

### Motherboard connections

- CPU → **socket**
- RAM → **RAM slots**
- Graphics/network cards → **expansion slots (PCI Express)**
- Storage → **SATA** or **PCI Express**
- Power → PSU connectors

**Hands-on:** Placed each component into its correct connection on a virtual motherboard. Low difficulty, high retention — the physical mapping reinforced the reading.

**Defender takeaway:** Every part has a job, which means every part is also a place something can fail or be protected.

---

## Lesson 3 — From Power Button to Operating System

### Boot sequence

```text
Power button → Firmware (UEFI) → POST → Boot device selection → Bootloader → Operating system