# TryHackMe : Operating System Introduction

**Series:** TryHackMe Room Walkthroughs · Room 05
**Platform:** [TryHackMe](https://tryhackme.com/)
**Module:** Operating System Introduction
**Focus:** Understanding the core duties of an OS, privilege layers, interfaces, and the OS landscape.
**Companion article:** [Hashnode](https://darajat.hashnode.dev/operating-systems-introduction)

> **Series note:** This is Room 05 of an ongoing TryHackMe Room Walkthroughs series. Each entry documents method and understanding, not flags or quiz answers, so the rooms keep their learning value for other beginners.

---

## Objective

Build a foundational understanding of what an Operating System (OS) is, how it manages hardware and software, the security mechanisms it enforces, and the different types of operating systems in the modern landscape.

---

## Scope & Ethics

This report documents method and understanding, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This is a study artifact, not a solution key.

---

## Environment

- Platform: TryHackMe, browser-based Ubuntu virtual machine
- Room type: Foundational theory with GUI practical exercises
- Prerequisite knowledge assumed: None, beginner-friendly

---

## Lesson 1 : Introduction to the Operating System

**Core idea:** The OS is the invisible manager that coordinates the chaos.

Without an operating system, every application would have to fight for direct control over the CPU, memory, and hardware. This would cause immediate conflicts. The OS sits between the user, the applications, and the physical hardware to keep everything running smoothly.

### System Privilege Layers
To prevent a single faulty app from crashing the entire machine, modern systems separate privileges into two zones:
1.  **Kernel Space:** The heavily guarded core. This is where the kernel (the brain of the OS) lives. It has unrestricted access to the CPU, RAM, and hardware.
2.  **User Space:** Where standard apps (like your web browser) run. These apps are blocked from touching the hardware directly. If an app needs to save a file, it must ask the kernel via a "system call."

---

## Lesson 2 : Operating System Duties & Security

**Core idea:** The OS does more than just look pretty; it enforces order and security.

The OS handles five core responsibilities:
1.  **Process Management:** Deciding which application gets CPU time and when.
2.  **Memory Management:** Allocating RAM to apps and reclaiming it when they close.
3.  **File System Management:** Organizing files, folders, and permissions.
4.  **User Management:** Handling logins and deciding who gets access to what.
5.  **Device Management:** Loading drivers so your mouse or printer just works.

### The Security Foundation
Before you even install an antivirus, the OS is already protecting you. It enforces:
- **Authentication:** Verifying your identity (passwords/biometrics).
- **Permissions:** Controlling what apps and users can read or write.
- **Isolation:** Keeping processes in their own secure boxes.
- **System Protection:** Guarding critical system files from tampering.

**Hands-on Practical:** 
I navigated a virtual Ubuntu machine using the GUI. I opened "About This Computer" to inspect the system specifications, memory allocation, and OS version. I also explored the System Monitor to view running processes and the file system.

---

## Lesson 3 : Operating System Interfaces

**Core idea:** You can talk to the OS in two different languages.

1.  **GUI (Graphical User Interface):** Point and click. It’s visual, intuitive, and great for everyday tasks (like finding a folder or opening a browser).
2.  **CLI (Command-Line Interface):** Text-based. You type exact commands. It’s faster, more powerful, and essential for advanced tasks and automation.

**Hands-on Practical:** 
I used the CLI to navigate the file system. Instead of clicking through folders, I used commands to list directory contents, proving how much faster the terminal can be once you know the syntax.

---

## Lesson 4 : The Operating System Landscape

**Core idea:** Different jobs require different tools.

There is no "one size fits all" OS. They are designed for specific environments:
- **Desktop:** Personal computers (Windows, macOS, Linux). Focused on user experience and graphics.
- **Server:** Web hosting and databases (Windows Server, Ubuntu Server). Focused on uptime and remote access (often no GUI).
- **Mobile:** Phones and tablets (Android, iOS). Focused on battery life, touch UI, and app sandboxing.
- **Embedded/IoT:** Smart TVs, routers, cars. Focused on minimal footprint and specific tasks.
- **Virtual/Cloud:** Containers and cloud instances. Focused on being lightweight and scalable.

---

## Lesson 5 : Real World Operating Systems

**Core idea:** The tech world is dominated by a few major families.

- **Windows:** The king of desktop computing. Also a massive player in enterprise servers.
- **macOS:** Known for its polished design and tight integration with Apple hardware.
- **Linux:** The open-source powerhouse. It’s not one OS, but a family of "distributions" (Ubuntu, Debian, Fedora). It absolutely dominates the web server and cloud markets.
- **Android & iOS:** The undisputed rulers of the mobile world.
- **Real-Time OS (RTOS):** Specialized systems for critical tasks (like aircraft controls) where a delay of even a millisecond is unacceptable.

**Hands-on Practical:**
I continued investigating the virtual machine. I checked the device types, navigated to specific user directories, and explored the Documents folder to find hidden file contents.

---

## Key Takeaways

| Concept | Meaning |
| --- | --- |
| The OS | The central manager coordinating hardware and software. |
| Kernel Space | The secure, privileged core of the OS. |
| User Space | The restricted area where apps run. |
| System Call | How a user app asks the kernel to do something. |
| GUI vs. CLI | Visual clicking vs. text-based commands. |
| OS Landscape | Desktop, Server, Mobile, Embedded, and Cloud. |

---

## Lessons Learned

- The OS is the ultimate middleman. It prevents apps from fighting over resources and keeps the system stable.
- Security starts at the OS level, long before you install third-party security tools.
- Learning the CLI is non-negotiable for cybersecurity. It gives you precision and speed that the GUI cannot match.
- Understanding the different OS families (Desktop vs. Server) is crucial because cybersecurity professionals must defend all of them.

---

## Next Steps

- Continue the TryHackMe Room Walkthroughs series. Next rooms: Windows Basics and Windows CLI Basics.
- Practice navigating both Linux and Windows systems using only the command line.
- Explore how permissions work at the file level in Linux (e.g., chmod, chown).

---

*Part of the TryHackMe Room Walkthroughs series. Companion article on Hashnode, link: (https://darajat.hashnode.dev/operating-systems-introduction)*

*Until then, keep exploring, keep experimenting, and keep learning.*
