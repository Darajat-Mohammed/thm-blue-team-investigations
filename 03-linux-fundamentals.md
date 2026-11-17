**TryHackMe — Linux Fundamentals**

**Series:** TryHackMe Room Walkthroughs · Room 03 **Platform:** [TryHackMe](https://tryhackme.com/) **Module:** Linux Fundamentals **Focus:** Navigating the Linux terminal, basic commands, file searching, and shell operators from a beginner's perspective **Companion article:** \[Hashnode, add link after publishing\]

> **Series note:** This is Room 03 of an ongoing TryHackMe Room Walkthroughs series. Each entry documents method and understanding, not flags or quiz answers, so the rooms keep their learning value for other beginners.

---

## Objective

Get comfortable with the Linux command line. Learn where Linux is used, how to identify your user, navigate the file system, search for data, and combine commands using shell operators.

---

## Scope & Ethics

This report documents method and understanding, not the room's flags or quiz answers. Answers are intentionally omitted so the room retains its learning value for others. This is a study artifact, not a solution key.

---

## Environment

- Platform: TryHackMe, browser-based Ubuntu lab machine
- Room type: Foundational, no live external target
- Prerequisite knowledge assumed: none, beginner-friendly

---

## Lesson 1 : Where is Linux Used?

**Core idea:** Linux is everywhere, even if you don't realize it.

The room opens by addressing the intimidation factor. Windows is familiar to most, but Linux powers a massive portion of the modern world. It is lightweight, flexible, and runs on everything from massive web servers to small devices.

You have likely used Linux today without knowing it. It powers:

- Websites you visit.
- Car entertainment and control panels.
- Point of Sale systems like checkout tills.
- Critical infrastructure like traffic lights and industrial sensors.
- Phones and small computing devices.

**Hands-on:** Started a browser-based Ubuntu lab machine to follow along with the room.

---

## Lesson 2 : Who Are You on This Machine?

**Core idea:** The terminal is where the real work happens.

In cybersecurity, you will spend most of your time in the command line interface, not clicking around with a mouse. A command is simply an instruction given to the computer.

The first command to learn is `whoami`.

- **Why it matters:** When you interact with a machine, you need to know who you are on the system. This tells you what access you have. In security, you will often switch between different users.

I ran `whoami` and the machine responded with the current user: `tryhackme`.

Next, I used `echo` to print text to the screen. I ran `echo "my name is darajat"`.

- **Why it matters:** `echo` is a building block. It is the foundation for sending and storing information in Linux, which becomes critical later.

---

## Lesson 3 : Finding Your Way Around

**Core idea:** Navigation is faster when your hands stay on the keyboard.

I had seen some of these commands before during my OverTheWire Bandit journey. This lesson solidified them.

| Command | What it does |
| --- | --- |
| `ls` | List what is in the current folder. |
| `cd` | Change directory. Move into a folder. |
| `cat` | Show the contents of a file. |
| `pwd` | Print working directory. Answers "where am I?" |

**Note:** Linux uses colors to help you. Folders are typically blue, which makes them easy to tell apart from files.

**Hands-on:** Navigated the file system using these commands and answered questions based on the output. It feels unfamiliar at first, but practice makes it faster than a mouse.

---

## Lesson 4 : Let the Machine Do the Searching

**Core idea:** Stop scrolling and start searching.

Real systems have millions of log lines and text files. You need tools to find the needle in the haystack quickly.

| Command | What it does |
| --- | --- |
| `find` | Searches for files by name. Example: `find -name passwords.txt` |
| `grep` | Searches inside files for specific text. Example: `grep "password123" passwords.txt` |

**Hands-on:** The room provided a web server log file called `access.log` with hundreds of lines. Somewhere inside was a flag. I used `grep THM access.log` to filter the noise and find the target instantly.

**Defender takeaway:** `grep` is an essential tool for log analysis. When reviewing server logs for suspicious activity, you will use this constantly.

---

## Lesson 5 : Shell Operators (Combining Commands)

**Core idea:** Use operators to connect commands and capture output.

Linux uses special characters to chain commands together and direct where the output goes.

| Operator | What it does |
| --- | --- |
| `&` | Runs a command in the background. You don't have to wait for it to finish before typing the next command. |
| `&&` | Runs the first command, waits for it to finish successfully, then runs the second. Like dominoes. |
| `>` | Redirects output to a file. This **overwrites** anything already in the file. |
| `>>` | Redirects output to a file, but **appends** to the bottom without deleting what was there. |

**Hands-on:**

1. I used `echo "TryHackMe" > thm` to save text to a file, overwriting anything that might have been there.
2. I used `echo "thm" >> thm` to add text to the same file.
3. I ran `cat thm` to check the result.
4. The output showed both lines. The `>>` operator added to the file without deleting the first line.

**Why it matters:** This is where the terminal becomes powerful. You are no longer just reading output; you are combining commands and saving results.

---

## Key Takeaways

| Concept | Meaning |
| --- | --- |
| Linux ubiquity | Linux runs servers, cars, PoS systems, and critical infrastructure. |
| `whoami` | Identifies your current user, which tells you your access level. |
| `echo` | Outputs text. The foundation for storing data in Linux. |
| Navigation | `ls`, `cd`, `cat`, `pwd` are the core commands for moving around. |
| Searching | `find` looks for files. `grep` searches inside them. |
| Shell operators | `&`, `&&`, `>`, `>>` combine commands and redirect output. |

---

## Lessons Learned

- The terminal is unavoidable in cybersecurity. It is faster and more powerful than a mouse once you get used to it.
- Knowing who you are (`whoami`) is the first step in any investigation or engagement.
- Searching is a core defensive skill. `grep` turns a massive log file into a readable story.
- Shell operators let you build workflows. You are no longer just consuming output; you are directing it.

---

## Next Steps

- Continue the TryHackMe Room Walkthroughs series. Next room to be confirmed.
- Practice chaining commands together (e.g., using `|` to pipe output from one command into another).
- Apply `grep` to larger log files to build muscle memory for SOC analysis.

---

*Part of the TryHackMe Room Walkthroughs series. Companion article on Hashnode, link to be added after publishing.*

*Until then, keep exploring, keep experimenting, and keep learning.*
