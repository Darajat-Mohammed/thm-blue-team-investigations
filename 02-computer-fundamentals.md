# Computer Fundamentals

**Series:** TryHackMe Room Walkthroughs · Room 02 **Platform:** [TryHackMe](https://tryhackme.com/) **Module:** Computer Fundamentals **Focus:** Hardware, system components, and the boot process, examined from a defender's perspective **Companion article:** https://darajat.hashnode.dev/computer-fundamentals

> **Series note:** This is Room 02 of an ongoing TryHackMe Room Walkthroughs series. Each entry documents method and understanding, not flags or quiz answers, so the rooms keep their learning value for other beginners.

---

## Objective

Build a working model of what a computer is made of, how the parts connect, and what happens between pressing the power button and the operating system taking over, with a security lens applied at each stage.

Three guiding questions were used throughout.

1. What are the parts?
2. How are they connected?
3. Who or what can reach each part, and how?

---

## Scope & Ethics

This report documents method and understanding, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This is a study artifact, not a solution key.

---

## Environment

- Platform: TryHackMe, web-based virtual environment
- Room type: Foundational, no live target
- Prerequisite knowledge assumed: none, beginner-friendly

---

## Lesson 1: Understanding What I'm Securing

**Core idea:** You cannot defend what you do not understand.

The room frames a computer as a castle. Before a guard can protect it, they need the floor plan. Where the treasure is, where supplies are stored, who may enter which room, and how anyone gets in. A guard who has never seen the castle cannot guard it.

**Defender takeaway:** Security work begins with inventory and architecture. The floor plan comes before the lock.

---

## Lesson 2: The Building Blocks Inside a Computer

Every computer, from laptop to server, is assembled from the same class of parts. Each part has a job, and the system only functions when all of them do theirs.

### Component reference

| Part | Function | Defender relevance |
| --- | --- | --- |
| Motherboard | Main circuit board. Every part connects through it. Firmware lives on it. | Central path for component traffic. Firmware is an early-code attack surface. |
| CPU | Executes instructions. Modern CPUs have multiple cores. | All software, legitimate or malicious, becomes CPU instructions. |
| RAM | Volatile working memory for whatever the CPU is actively using. | Can hold passwords and keys in use. Volatile, so memory capture precedes shutdown in investigations. |
| SSD / HDD | Persistent storage. HDD has moving parts and is cheaper per GB. SSD has no moving parts and is faster. | Where data persists. Lost or stolen drives are why disk encryption matters. |
| Network adapter | Connects the machine to other machines, wired or Wi-Fi. | The machine's network doorway. Ties into networking fundamentals. |
| Power supply (PSU) | Converts wall power and distributes it to components. | Failure means availability loss. |
| Graphics card | Renders output. Excels at parallel computation. | GPU parallelism is why password-cracking tools leverage GPUs. |
| Input/output devices | Keyboards, mice, microphones in. Monitors, printers, speakers out over USB, HDMI, DisplayPort. | Every port is an entry point. A plugged-in USB device is a classic attack vector. |

### RAM vs. storage. The desk and the filing cabinet.

- **RAM is the desk.** Small, instantly accessible, cleared at end of day. Volatile.
- **Storage is the filing cabinet.** Large, persistent across power loss.

Programs and open files are loaded from storage into RAM while in use. When power is lost, the desk is wiped. The cabinet remains. RAM generations such as DDR4 and DDR5 differ in speed.

### Storage types

- **HDD:** spinning platter with a moving arm. Like a record player.
- **SSD:** no moving parts. Like a large USB stick. Far faster.

### Motherboard connections

- CPU goes into the **socket**.
- RAM goes into **RAM slots**.
- Graphics and network cards go into **expansion slots**, PCI Express.
- Storage connects through **SATA** or **PCI Express**.
- Power comes from **PSU connectors**.

**Hands-on:** Placed each component into its correct connection on a virtual motherboard. Low difficulty, high retention. The physical mapping reinforced the reading.

**Defender takeaway:** Every part has a job, which means every part is also a place something can fail or be protected.

---

## Lesson 3: From Power Button to Operating System

### Boot sequence

Power button → Firmware (UEFI) → POST → Boot device selection → Bootloader → Operating system

### Step by step

**1\. Power button.** The PSU begins distributing power. Nothing is executing yet.

> **Defender view:** Physical access to the machine grants extensive options.

**2\. Firmware, UEFI or BIOS.** First code to run. Initializes components before any OS exists. UEFI is the modern successor to legacy BIOS.

> **Defender view:** First code executed, so everything after must trust it. **Secure Boot**, a UEFI feature, verifies startup software before allowing it to run.

**3\. POST, Power-On Self-Test.** Health check confirming required components are present, configured, and working. Failures surface as beeps or error messages.

**4\. Boot device selection.** Firmware walks an ordered list of devices looking for boot instructions.

> **Defender view:** If an attacker alters the order or boots from removable media, they can start the machine with their own software. Firmware settings are often password-protected for this reason.

**5\. Bootloader.** Loads the OS core into RAM and transfers control.

> **Defender view:** Malware at this stage, a bootkit, executes before the OS and before OS-level security tooling.

### Chain of trust

Each step trusts the one before it. The earlier a stage is tampered with, the harder it is to detect, because everything downstream must trust it. This is the chain of trust.

---

## Key Takeaways

| Concept | Meaning |
| --- | --- |
| Castle thinking | You can't defend what you don't understand. The floor plan comes first. |
| Volatile memory | RAM empties on power loss. Capture it before shutdown during investigation. |
| Storage | Persistent data lives on SSD or HDD. Disk encryption matters. |
| Ports and adapters | Every connection is a potential way in. |
| UEFI / BIOS | First software to run. Initializes hardware. |
| POST | Self-check that required components are present and working. |
| Boot order | The firmware's ordered list of boot locations. |
| Bootloader | Loads the OS into RAM and hands over control. |
| Secure Boot | UEFI feature verifying startup software is trusted. |

The three questions applied to every part and every step.

1. What are the parts?
2. How are they connected?
3. Who or what can reach each one, and how?

---

## Lessons Learned

- Security starts with understanding. Inventory and architecture before controls.
- RAM is volatile and can hold secrets in use. Capture before shutdown.
- Every physical and logical connection is a potential entry point.
- The boot process is a chain of trust. Compromise early means compromise that is hard to detect.
- Firmware and bootloader stages sit below OS-level defenses. A real blind spot to know about.

---

## Next

- Continue the TryHackMe Room Walkthroughs series. Next room to be confirmed.

---

*Part of the TryHackMe Room Walkthroughs series. Companion article on Hashnode, link: https://darajat.hashnode.dev/computer-fundamentals*

*Until then, keep exploring, keep experimenting, keep learning.*
