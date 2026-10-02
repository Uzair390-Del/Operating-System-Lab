# Operating Systems Lab — Lab 02

## Windows CMD: File, Directory, Network & System Commands

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6?logo=windows&logoColor=white)
![Tool](https://img.shields.io/badge/Tool-Command%20Prompt-000000?logo=windowsterminal&logoColor=white)
![Duration](https://img.shields.io/badge/Duration-3%20Hours-blue)
![Bloom](https://img.shields.io/badge/Bloom%20Level-C3-orange)

---

## Table of Contents

1. [Lab Information](#1-lab-information)
2. [Learning Objectives](#2-learning-objectives)
3. [Introduction](#3-introduction)
4. [Command Prompt Fundamentals](#4-command-prompt-fundamentals)
5. [File and Directory Commands](#5-file-and-directory-commands)
6. [Wildcards and Directory Tree](#6-wildcards-and-directory-tree)
7. [Network Commands](#7-network-commands)
8. [System Commands](#8-system-commands)
9. [Practical Demonstrations](#9-practical-demonstrations)
10. [Worked Examples](#10-worked-examples)
11. [Practical Questions with Solutions](#11-practical-questions-with-solutions)
12. [Student Hands-On Activity](#12-student-hands-on-activity)
13. [Instructor Solution](#13-instructor-solution)
14. [Common Student Mistakes](#14-common-student-mistakes)
15. [Safety Notes](#15-safety-notes)
16. [Instructor Notes](#16-instructor-notes)
17. [Quick Knowledge Check](#17-quick-knowledge-check)
18. [Viva Questions](#18-viva-questions)
19. [Lab Task and Submission](#19-lab-task-and-submission)
20. [Lecture Summary](#20-lecture-summary)
21. [Command Cheat Sheet](#21-command-cheat-sheet)
22. [Connection to Lab 3](#22-connection-to-lab-3)

---

## 1. Lab Information

| Item | Details |
| --- | --- |
| **Course** | Operating Systems – Lab |
| **Lab No.** | Lab 02 |
| **Title** | Windows CMD: File, Directory, Network & System Commands |
| **Main Platform** | Microsoft Windows 10/11 |
| **Suggested Duration** | 3 Hours |
| **Required Tool** | Command Prompt (CMD) |
| **Prerequisite** | Lab 1: Windows Overview, Tools & Shortcuts |
| **Main CLO** | CLO-4 — Demonstrate knowledge in applying system software and tools available in modern operating systems |
| **Supporting CLO** | CLO-1 — Understand core functions of operating systems |
| **Relevant PLOs** | PLO-02, PLO-05 |
| **Bloom Level** | C3 — Demonstrate / Apply |

---

## 2. Learning Objectives

By the end of this lab, students will be able to:

- **Explain** what Command Prompt is and why command-line interfaces are useful.
- **Navigate** between drives and directories using CMD commands.
- **Create, copy, move, rename, and delete** files and directories.
- **Use** basic Windows network commands to identify IP configuration and host information.
- **Use** system commands to inspect Windows information and running processes.
- **Demonstrate** command-line problem-solving using a realistic file-management scenario.

---

## 3. Introduction

Microsoft Windows provides both a **Graphical User Interface (GUI)** and command-line tools for interacting with the operating system.

In Lab 1, students used tools such as File Explorer, Task Manager, Run, and System Information. In this lab, the same operating system is controlled using **Command Prompt**, commonly called **CMD**.

Instead of clicking folders and menus, students will type commands such as:

```text
dir
cd
mkdir
copy
move
del
ipconfig
hostname
tasklist
```

Command-line interfaces are important because they are fast, precise, useful for troubleshooting, and can later be automated using **Batch Scripts**.

---

## 4. Command Prompt Fundamentals

### 4.1 What is Command Prompt?

**Command Prompt** is a Windows command-line interpreter that allows users to interact with the operating system by typing commands.

It is commonly represented by:

```text
cmd.exe
```

- `cmd` means **Command**
- `.exe` means **executable program**

### 4.2 GUI vs CLI

A **GUI** uses graphical elements such as icons, menus, buttons, and windows. A **CLI** uses typed commands.

| GUI | CLI |
| --- | --- |
| Uses mouse and menus | Uses text commands |
| Easier for beginners | Faster for experienced users |
| Visual interaction | Precise command interaction |
| Good for routine tasks | Good for automation/troubleshooting |
| File Explorer | CMD |

**Example — creating a folder**

| Interface | Action |
| --- | --- |
| GUI | Right-click → New → Folder |
| CLI | `mkdir OS_Lab` |

Both ultimately request the operating system to create a directory.

### 4.3 How to Open Command Prompt

| Method | Steps |
| --- | --- |
| **1. Run Dialog** | Press `Win + R`, type `cmd`, then press **Enter** |
| **2. Start Search** | Press the Windows key, type `Command Prompt`, then open it |
| **3. Administrator Mode** | Search for **Command Prompt**, then select **Run as administrator** |

> **Important:** Administrator mode provides elevated privileges. For today's file-management exercises, students should generally use **normal CMD** unless the instructor specifically requires administrator privileges.

### 4.4 Understanding the CMD Prompt

After opening CMD, you may see:

```text
C:\Users\Student>
```

| Part | Meaning |
| --- | --- |
| `C:` | The current drive |
| `\Users\Student` | The current directory path |
| `>` | CMD is ready to accept a command |

Therefore, `C:\Users\Student>` means the user is currently working inside the **Student** directory located inside **Users** on drive **C:**.

---

## 5. File and Directory Commands

### 5.1 `dir` — Display Directory Contents

| | |
| --- | --- |
| **Meaning** | `dir` stands for **directory** |
| **Purpose** | Displays files and subdirectories in the current directory |

**Syntax**

```text
dir
dir <path>
```

**Example**

```text
dir
```

**Expected output** may contain `Documents`, `Downloads`, `Desktop`, `Pictures`, `Videos`, plus files, sizes, dates, and free-space information.

### 5.2 `cd` — Change Directory

| | |
| --- | --- |
| **Meaning** | `cd` means **Change Directory** |
| **Purpose** | Changes the current working directory |

**Syntax**

```text
cd <directory_name>
```

**Example**

```text
cd Documents
```

If the current location is `C:\Users\Student>`, the prompt becomes `C:\Users\Student\Documents>`.

#### Moving Back One Directory — `cd ..`

`..` represents the **parent directory**.

```text
C:\Users\Student\Documents> cd ..
C:\Users\Student>
```

#### Moving to the Root Directory — `cd \`

`\` represents the root of the current drive.

```text
cd \
```

Result: `C:\>`

### 5.3 `cls` — Clear Screen

| | |
| --- | --- |
| **Meaning** | `cls` means **Clear Screen** |
| **Purpose** | Clears previous commands and output from the Command Prompt display |

> **Important:** It does **not** delete files or commands from the operating system. It only clears the visible terminal screen.

### 5.4 `mkdir` — Create Directory

| | |
| --- | --- |
| **Command** | `mkdir` (short form: `md`) |
| **Meaning** | Make Directory |
| **Purpose** | Creates a new directory |

**Syntax**

```text
mkdir <directory_name>
```

**Example**

```text
mkdir OS_Lab
```

**Result:** A directory named `OS_Lab` is created in the current directory.

#### Creating a Folder with Spaces

To create a folder named `Operating Systems Lab`, use quotation marks:

```text
mkdir "Operating Systems Lab"
```

**Why quotes?** CMD may otherwise interpret spaces as separators between arguments.

### 5.5 `rmdir` — Remove Directory

| | |
| --- | --- |
| **Command** | `rmdir` (short form: `rd`) |
| **Purpose** | Removes a directory |

**Example**

```text
rmdir TestFolder
```

> **Important:** Normally, the directory must be empty. For classroom safety, students should remove only folders they created themselves.

### 5.6 `echo` — Display Text

| | |
| --- | --- |
| **Purpose** | Displays text in CMD |

**Example**

```text
echo Welcome to Operating Systems Lab
```

**Output**

```text
Welcome to Operating Systems Lab
```

#### Creating a File Using `echo`

A simple text file can be created using redirection:

```text
echo Operating Systems Lab > notes.txt
```

| Part | Meaning |
| --- | --- |
| `echo Operating Systems Lab` | Produces the text `Operating Systems Lab` |
| `>` | Redirects the output into a file |
| `notes.txt` | The destination file |

**Result:** A file named `notes.txt` is created, containing `Operating Systems Lab`.

### 5.7 `type` — Display File Contents

| | |
| --- | --- |
| **Purpose** | Displays the contents of a text file |

**Syntax**

```text
type <filename>
```

**Example**

```text
type notes.txt
```

**Output**

```text
Operating Systems Lab
```

### 5.8 `copy` — Copy a File

| | |
| --- | --- |
| **Purpose** | Creates a duplicate of a file in another location or under another name |

**Syntax**

```text
copy <source> <destination>
```

**Example**

```text
copy notes.txt backup.txt
```

- `notes.txt` = source file
- `backup.txt` = destination file

**Result:** Two files now exist: `notes.txt` and `backup.txt`.

#### Copying a File to Another Folder

Suppose we have `C:\OSLab\notes.txt` and a folder `C:\OSLab\Backup`:

```text
copy notes.txt Backup
```

The file is copied into the `Backup` directory.

### 5.9 `move` — Move a File

| | |
| --- | --- |
| **Purpose** | Moves a file or directory from one location to another |

**Syntax**

```text
move <source> <destination>
```

**Example**

```text
move notes.txt Documents
```

**Result:** `notes.txt` is removed from the current location and placed inside the `Documents` directory.

### 5.10 Copy vs Move

| Command | Result |
| --- | --- |
| `copy` | Original remains; duplicate is created |
| `move` | Original item changes location |

```text
copy report.txt Backup
```
→ Original `report.txt` remains, **plus** another `report.txt` exists in `Backup`.

```text
move report.txt Backup
```
→ The file now resides **only** in `Backup`.

### 5.11 `ren` — Rename File or Directory

| | |
| --- | --- |
| **Full meaning** | Rename |

**Syntax**

```text
ren <old_name> <new_name>
```

**Example**

```text
ren notes.txt os_notes.txt
```

**Result:** `notes.txt` becomes `os_notes.txt`.

### 5.12 `del` — Delete File

| | |
| --- | --- |
| **Meaning** | Delete |
| **Purpose** | Deletes one or more files |

**Example**

```text
del test.txt
```

> **Warning:** Command-line deletion may not behave like ordinary File Explorer deletion to the Recycle Bin. Students should only delete **practice files**.

---

## 6. Wildcards and Directory Tree

### 6.1 Wildcards in CMD

Two common wildcard characters are `*` and `?`.

#### `*` — Multiple Characters

```text
dir *.txt
```

Displays files ending in `.txt`. Possible matches: `notes.txt`, `report.txt`, `student.txt`.

#### `?` — One Character

```text
dir file?.txt
```

| Matches | Does not match |
| --- | --- |
| `file1.txt` | `file10.txt` |
| `file2.txt` | |
| `fileA.txt` | |

`file10.txt` is not matched because `?` represents exactly **one** character.

### 6.2 `tree` — Display Directory Structure

| | |
| --- | --- |
| **Purpose** | Displays folders in a hierarchical tree structure |

**Example**

```text
tree
```

**Possible output**

```text
OSLab
├── Documents
├── Backup
└── Assignment
```

This makes directory organization easier to visualize.

---

## 7. Network Commands

Command Prompt also provides useful networking tools. These commands help administrators and technicians inspect the computer's network configuration.

### 7.1 `hostname`

| | |
| --- | --- |
| **Purpose** | Displays the computer's network host name |

```text
hostname
```

**Possible output:** `LAB-PC-07`

**Real-world use:** An administrator may ask, *"What is the hostname of the affected computer?"* Instead of checking through several menus, the user can simply execute `hostname`.

### 7.2 `ipconfig`

| | |
| --- | --- |
| **Meaning** | IP Configuration |
| **Purpose** | Displays basic TCP/IP configuration for network adapters |

```text
ipconfig
```

Possible information includes **IPv4 Address**, **Subnet Mask**, and **Default Gateway**.

**Example output**

```text
IPv4 Address . . . . : 192.168.1.25
Subnet Mask  . . . . : 255.255.255.0
Default Gateway  . . : 192.168.1.1
```

### 7.3 `ipconfig /all`

```text
ipconfig /all
```

The `/all` option requests more detailed configuration information. It may display:

- Host name
- Adapter information
- Physical/MAC address
- DHCP information
- IPv4/IPv6 addresses
- DNS servers
- Default gateway

> **Important:** The slash `/` introduces an **option/switch** for many Windows commands.

### 7.4 `ping`

| | |
| --- | --- |
| **Purpose** | Tests basic IP connectivity to another host and measures response information |

```text
ping 127.0.0.1
```

**What is `127.0.0.1`?** It is the IPv4 **loopback address**, representing the local computer's own network stack.

**Possible output**

```text
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
```

#### Ping a Hostname

```text
ping google.com
```

This attempts to resolve the hostname and send ICMP Echo Requests.

> **Important:** A failed ping does **not always mean that the target is offline**. Some networks or hosts block ICMP traffic.

### 7.5 `nslookup`

| | |
| --- | --- |
| **Purpose** | Queries DNS information |
| **DNS** | Domain Name System |

```text
nslookup example.com
```

The command may display the resolved IP address and DNS server information.

### 7.6 `tracert`

| | |
| --- | --- |
| **Meaning** | Trace Route |
| **Purpose** | Shows network hops between your computer and a destination |

```text
tracert example.com
```

This can help identify where connectivity or latency problems occur.

---

## 8. System Commands

Now we inspect Windows itself.

### 8.1 `systeminfo`

| | |
| --- | --- |
| **Purpose** | Displays detailed operating-system and system information |

```text
systeminfo
```

Possible information includes:

- Host Name
- OS Name
- OS Version
- System Manufacturer
- System Model
- System Type
- Processor
- BIOS information
- Installed memory

> This command can produce substantial output.

### 8.2 `whoami`

| | |
| --- | --- |
| **Meaning** | *Who am I?* |
| **Purpose** | Displays the currently logged-in user identity |

```text
whoami
```

**Possible output:** `labpc\student`

This tells us the computer/domain context and user account.

### 8.3 `tasklist`

| | |
| --- | --- |
| **Purpose** | Displays running processes |

```text
tasklist
```

**Possible output**

```text
Image Name          PID
notepad.exe         5420
explorer.exe        2136
```

**Important terms**

| Term | Meaning |
| --- | --- |
| **Image Name** | Process executable name |
| **PID** | Process Identifier — every running process is assigned a process ID |

---

## 9. Practical Demonstrations

### Demonstration 1 — Build a Lab Folder Structure

**Objective:** Create and manage folders using only CMD.

```text
:: Step 1 — Create a main directory
mkdir OS_Lab2

:: Step 2 — Enter it
cd OS_Lab2

:: Step 3 — Create three directories
mkdir Notes
mkdir Assignments
mkdir Backup

:: Step 4 — Display directories
dir

:: Step 5 — Display structure
tree
```

**Expected structure**

```text
OS_Lab2
├── Notes
├── Assignments
└── Backup
```

### Demonstration 2 — Create and Manage Files

```text
:: Create a text file
echo Operating Systems Lab 2 > notes.txt

:: Display it
type notes.txt

:: Copy it
copy notes.txt Backup

:: Rename original
ren notes.txt commands.txt

:: Move it
move commands.txt Notes

:: Check
tree /f
```

> The `/f` option tells `tree` to display **files as well as folders**.

### Demonstration 3 — Network Information

```text
hostname
ipconfig
ping 127.0.0.1
```

Record the **hostname**, **IPv4 Address**, **Subnet Mask**, and **Default Gateway**.

**Learning point:** Students are using built-in Windows commands to investigate the computer's networking environment.

### Demonstration 4 — System Investigation

```text
whoami
systeminfo
tasklist
```

Students should identify:

- Current user
- OS name
- OS version
- Installed RAM
- One running process
- PID of that process

---

## 10. Worked Examples

### 10.1 Basic Example

**Problem:** Create a folder named `Semester` and enter it.

**Solution**

```text
mkdir Semester
cd Semester
```

**Explanation:** `mkdir Semester` creates the folder; `cd Semester` changes the current working directory to that folder.

### 10.2 Intermediate Example

**Problem:** Create the following structure:

```text
OS
├── Lectures
├── Labs
└── Backup
```

**Solution**

```text
mkdir OS
cd OS
mkdir Lectures
mkdir Labs
mkdir Backup
tree
```

**Explanation:** Each `mkdir` creates one directory. `tree` verifies the final hierarchy.

### 10.3 Real-World Problem-Based Example

**Scenario:** You work in an IT support department. A user's computer is connected to the network, but they report network-access problems. Your supervisor requests:

- Computer hostname
- IPv4 address
- Default gateway
- Test of local TCP/IP
- Test of another host
- Windows system information

**Solution**

```text
hostname
ipconfig
ping 127.0.0.1
ping <default_gateway>
systeminfo
```

> `ping <default_gateway>` tests another permitted destination, for example your lab gateway.

**Reasoning:** Each command answers a different diagnostic question.

| Command | Diagnostic question |
| --- | --- |
| `hostname` | Which machine is this? |
| `ipconfig` | What is the network configuration? |
| `ping` | Is basic reachability working? |
| `systeminfo` | What are the OS/system details? |

---

## 11. Practical Questions with Solutions

### Question 1 — Basic

Display the contents of your current directory.

```text
dir
```

### Question 2 — Basic

Create a folder called `PF_Lab`.

```text
mkdir PF_Lab
```

### Question 3 — Intermediate

Create a text file called `student.txt` containing `Operating Systems`.

```text
echo Operating Systems > student.txt
```

Then verify:

```text
type student.txt
```

### Question 4 — Intermediate

Rename `student.txt` to `os_student.txt`.

```text
ren student.txt os_student.txt
```

### Question 5 — Problem Solving

You need to find the **computer name**, **IP address**, **current logged-in user**, and **Windows version**. Which commands should you use?

```text
hostname
ipconfig
whoami
systeminfo
```

---

## 12. Student Hands-On Activity

### Scenario — Organize a Student Project

You have been given several project files and need to organize them using **CMD only**.

**Requirements**

Create this structure:

```text
Student_Project
├── Source
├── Documents
└── Backup
```

Inside `Documents`, create `readme.txt` with the text:

```text
Operating Systems Project
```

Then:

- [ ] Copy `readme.txt` to `Backup`.
- [ ] Rename the original file to `project_info.txt`.
- [ ] Display the final directory tree including files.
- [ ] Display your hostname.
- [ ] Display your IPv4 configuration.

---

## 13. Instructor Solution

One possible solution:

```text
mkdir Student_Project
cd Student_Project
mkdir Source
mkdir Documents
mkdir Backup
cd Documents
echo Operating Systems Project > readme.txt
copy readme.txt ..\Backup
ren readme.txt project_info.txt
cd ..
tree /f
hostname
ipconfig
```

### Line-by-Line Explanation

| Command | Explanation |
| --- | --- |
| `mkdir Student_Project` | Creates the main project directory |
| `cd Student_Project` | Moves into the new directory |
| `mkdir Source` | Creates the Source folder |
| `mkdir Documents` | Creates the Documents folder |
| `mkdir Backup` | Creates the Backup folder |
| `cd Documents` | Moves into Documents |
| `echo Operating Systems Project > readme.txt` | Creates `readme.txt` and writes text into it |
| `copy readme.txt ..\Backup` | Copies the file to the Backup folder |
| `ren readme.txt project_info.txt` | Renames the original file |
| `cd ..` | Returns to `Student_Project` |
| `tree /f` | Displays the directory structure and files |
| `hostname` | Displays the computer name |
| `ipconfig` | Displays network configuration |

**Understanding `..\Backup`:** `..` means the parent directory, so `..\Backup` means *go one level up, then enter Backup*.

---

## 14. Common Student Mistakes

### Mistake 1 — Using `cd` to create folders

```text
:: Incorrect (Test does not exist)
cd Test

:: Correct — create it first, then enter it
mkdir Test
cd Test
```

### Mistake 2 — Forgetting quotation marks

```text
:: Incorrect — may be interpreted as separate arguments
mkdir Operating Systems

:: Safer
mkdir "Operating Systems"
```

### Mistake 3 — Confusing `copy` and `move`

- `copy` **duplicates**.
- `move` **changes location**.

### Mistake 4 — Deleting the wrong file

Always check with `dir` before executing `del`.

### Mistake 5 — Assuming ping failure always means no internet

Ping may fail because:

- ICMP is blocked.
- Firewall rules prevent responses.
- DNS resolution fails.
- Destination is unavailable.
- Network route has a problem.

---

## 15. Safety Notes

> **Use only the practice directory created during the lab.**

- Avoid commands such as `del *` or recursive deletion on important folders.
- Do not terminate unknown processes.
- Do not modify protected Windows directories.
- Do not execute unfamiliar commands with Administrator privileges.

---

## 16. Instructor Notes

A good way to teach this lab is to **compare every major CMD operation with the GUI equivalent**.

| GUI | CMD |
| --- | --- |
| Right-click → New Folder | `mkdir OS_Lab` |

Then ask: *Which method would be easier to automate for 100 folders?* Students will quickly understand why command-line tools matter.

**Suggested live demonstration**

1. Open File Explorer.
2. Open CMD.
3. Create a folder using CMD.
4. Refresh File Explorer.
5. Show students that the folder appears immediately.

**Explain:** CMD and File Explorer are simply two interfaces asking the same operating system/file system to perform operations.

---

## 17. Quick Knowledge Check

| # | Question | Answer |
| --- | --- | --- |
| Q1 | What does CMD stand for? | Command Prompt / command interpreter environment |
| Q2 | Which command displays directory contents? | `dir` |
| Q3 | Which command changes directory? | `cd` |
| Q4 | How do you move one directory back? | `cd ..` |
| Q5 | Which command creates a folder? | `mkdir` |
| Q6 | Which command displays your IP configuration? | `ipconfig` |
| Q7 | Which command displays the hostname? | `hostname` |
| Q8 | Which command displays running processes? | `tasklist` |
| Q9 | Which command displays the current user? | `whoami` |
| Q10 | What does `>` do in an `echo` command? | Redirects output to a file |

---

## 18. Viva Questions

| # | Question | Answer |
| --- | --- | --- |
| Q1 | What is Command Prompt? | A text-based Windows command-line interface used to execute commands |
| Q2 | What does `dir` do? | Displays files and directories |
| Q3 | Explain `cd ..` | It moves to the parent directory |
| Q4 | Difference between `mkdir` and `rmdir`? | `mkdir` creates a directory; `rmdir` removes one |
| Q5 | Difference between `copy` and `move`? | Copy duplicates an item, while move changes its location |
| Q6 | What does `ipconfig` provide? | Windows TCP/IP configuration information |
| Q7 | What is an IPv4 address? | A 32-bit logical network address used to identify a host/interface on an IPv4 network |
| Q8 | What does `ping` test? | Basic IP reachability and response timing |
| Q9 | What is a PID? | A Process Identifier assigned to a running process |
| Q10 | Why is CMD useful in operating systems? | It provides direct, efficient, scriptable access to system operations and tools |

---

## 19. Lab Task and Submission

### Task — CMD System and File Management

Using Command Prompt **only**, create:

```text
OS_Assignment
├── Theory
├── Lab
└── Backup
```

Inside `Lab`, create `lab2.txt` containing:

```text
Windows CMD Practical
```

**Perform the following:**

- [ ] Display the contents of `lab2.txt`.
- [ ] Copy it to `Backup`.
- [ ] Rename the original to `cmd_lab.txt`.
- [ ] Display the complete tree including files.
- [ ] Record your hostname.
- [ ] Record IPv4 address.
- [ ] Record current user.
- [ ] Record Windows OS name/version.
- [ ] Record any two running processes and their PIDs.

### Submission Requirements

Students should provide:

- Commands used
- Screenshots/output
- Final directory structure
- Short explanation of each major command

---

## 20. Lecture Summary

In this lab, students learned how to interact with Windows using the **Command Prompt**. The major areas covered were:

```text
Navigation
    ↓
File Management
    ↓
Directory Management
    ↓
Network Information
    ↓
System Information
    ↓
Process Inspection
```

**Core commands:**
`dir` · `cd` · `mkdir` · `rmdir` · `echo` · `type` · `copy` · `move` · `ren` · `del` · `tree` · `hostname` · `ipconfig` · `ping` · `nslookup` · `tracert` · `systeminfo` · `whoami` · `tasklist`

> **Key learning point:** CMD is not just a collection of commands. It is a **direct text-based interface to operating-system services**, and it becomes the foundation for automation in the next labs.

---

## 21. Command Cheat Sheet

| Command | Purpose | Example |
| --- | --- | --- |
| `dir` | Display directory contents | `dir` |
| `cd` | Change directory | `cd Documents` |
| `cd ..` | Parent directory | `cd ..` |
| `cd \` | Root directory | `cd \` |
| `cls` | Clear CMD screen | `cls` |
| `mkdir` | Create directory | `mkdir OS_Lab` |
| `rmdir` | Remove empty directory | `rmdir Test` |
| `echo` | Display/write text | `echo Hello` |
| `type` | Read text file | `type notes.txt` |
| `copy` | Copy file | `copy a.txt Backup` |
| `move` | Move file | `move a.txt Documents` |
| `ren` | Rename item | `ren a.txt b.txt` |
| `del` | Delete file | `del test.txt` |
| `tree` | Show directory hierarchy | `tree /f` |
| `hostname` | Display computer name | `hostname` |
| `ipconfig` | Network configuration | `ipconfig` |
| `ipconfig /all` | Detailed network configuration | `ipconfig /all` |
| `ping` | Test basic connectivity | `ping 127.0.0.1` |
| `nslookup` | Query DNS | `nslookup example.com` |
| `tracert` | Trace route | `tracert example.com` |
| `systeminfo` | System/OS information | `systeminfo` |
| `whoami` | Current user | `whoami` |
| `tasklist` | Running processes | `tasklist` |

---

## 22. Connection to Lab 3

Lab 2 teaches students how to perform Windows operations **one command at a time**. The next major step is automation:

```text
Manual Commands
      ↓
Sequence of Commands
      ↓
Batch File
      ↓
Conditions
      ↓
Loops
      ↓
Automation
```

The natural next lecture is **Lab 3 — Batch Scripting**, where these individual commands are combined into automated scripts.

---

<p align="center"><b>Operating Systems Lab · Lab 02</b><br>Windows CMD: File, Directory, Network &amp; System Commands</p>
