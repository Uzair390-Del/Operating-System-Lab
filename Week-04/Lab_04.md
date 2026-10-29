# Operating Systems Lab — Lab 04

## PowerShell Commands, Scripting & System Administration

---

## Lab Information

| Item | Details |
| --- | --- |
| **Course** | Operating Systems – Lab |
| **Lab No.** | Lab 04 |
| **Title** | PowerShell Commands, Scripting & System Administration |
| **Main Platform** | Microsoft Windows 10 / 11 |
| **Suggested Duration** | 3 hours |
| **Required Tools** | Windows PowerShell or PowerShell 7, Windows Terminal, Notepad or VS Code |
| **Prerequisites** | Lab 2: CMD Commands · Lab 3: Batch Scripting |
| **Main CLO** | CLO-4 — Demonstrate knowledge in applying system software and tools available in modern operating systems |
| **Supporting CLO** | CLO-1 — Understand core OS functions and operating-system tools |
| **Relevant PLOs** | PLO-02, PLO-05 |
| **Bloom Level** | C3 — Demonstrate / Apply |

---

## Table of Contents

**Part A — Foundations**
1. [Learning Objectives](#1-learning-objectives)
2. [Introduction: Why PowerShell?](#2-introduction-why-powershell)
3. [What is PowerShell?](#3-what-is-powershell)
4. [PowerShell vs CMD vs Batch](#4-powershell-vs-cmd-vs-batch)
5. [Cmdlets and the Verb-Noun Pattern](#5-cmdlets-and-the-verb-noun-pattern)
6. [Opening PowerShell and Reading the Prompt](#6-opening-powershell-and-reading-the-prompt)
7. [Anatomy of a PowerShell Command](#7-anatomy-of-a-powershell-command)

**Part B — Learning to Learn**
8. [Get-Help — Built-in Documentation](#8-get-help--built-in-documentation)
9. [Get-Command — Discovering Commands](#9-get-command--discovering-commands)
10. [Aliases](#10-aliases)

**Part C — Files and Directories**
11. [Navigation: Get-Location, Set-Location, Get-ChildItem](#11-navigation-get-location-set-location-get-childitem)
12. [Creating Items: New-Item](#12-creating-items-new-item)
13. [Working with File Content](#13-working-with-file-content-set-content-add-content-get-content)
14. [Copy, Move, Rename, Remove](#14-copy-move-rename-and-remove)
15. [Practical 1 — Folder Structure](#15-practical-1--create-a-complete-folder-structure)
16. [Practical 2 — Create and Manage a Text File](#16-practical-2--create-and-manage-a-text-file)

**Part D — Variables and Input/Output**
17. [Variables](#17-variables)
18. [Write-Output and Read-Host](#18-write-output-and-read-host)
19. [String Interpolation](#19-string-interpolation)
20. [Practical 3 — Student Information Script](#20-practical-3--student-information-script)

**Part E — Processes and Services**
21. [Processes](#21-processes-get-process-start-process-stop-process)
22. [Practical 4 — Process Management](#22-practical-4--process-management)
23. [Windows Services](#23-windows-services-and-get-service)

**Part F — The Pipeline**
24. [The Pipeline](#24-the-pipeline)
25. [Where-Object and Comparison Operators](#25-where-object-and-comparison-operators)
26. [Sort-Object and Select-Object](#26-sort-object-and-select-object)
27. [A Powerful Pipeline Example](#27-a-powerful-pipeline-example)

**Part G — System and Network Information**
28. [System Information](#28-system-information-get-computerinfo)
29. [Network Information](#29-network-information)
30. [Practical 5 — Basic System Audit](#30-practical-5--basic-system-audit)

**Part H — Control Flow**
31. [If / Else](#31-if--else-decision-making)
32. [Practical 6 — Administrator Check](#32-practical-6--administrator-check-scenario)
33. [Loops: for and foreach](#33-loops-for-and-foreach)

**Part I — Scripting and Automation**
34. [PowerShell Scripts (.ps1)](#34-powershell-scripts-ps1)
35. [Execution Policy](#35-running-scripts-and-execution-policy)
36. [Test-Path and Out-File](#36-test-path-and-out-file)
37. [Practical 7 — Student Record Automation](#37-practical-7--student-record-automation)
38. [Complete Automation Example](#38-complete-automation-example-system-report)

**Part J — Applied Practice**
39. [Worked Examples](#39-worked-examples)
40. [Practical Questions with Solutions](#40-practical-questions-with-solutions)
41. [Student Hands-On Activity — IT System Audit](#41-student-hands-on-activity--it-system-audit)
42. [Instructor Solution and Line-by-Line Explanation](#42-instructor-solution-and-line-by-line-explanation)

**Part K — Quality, Safety and Assessment**
43. [Common Student Mistakes](#43-common-student-mistakes)
44. [Troubleshooting Guide](#44-troubleshooting-guide)
45. [Safety Notes](#45-important-safety-notes)
46. [Instructor Notes](#46-instructor-notes)
47. [Quick Knowledge Check](#47-quick-knowledge-check)
48. [Viva Questions](#48-viva-questions)
49. [Lab Task / Submission](#49-lab-task--submission)

**Part L — Wrap-Up**
50. [Lecture Summary](#50-lecture-summary)
51. [PowerShell Cheat Sheet](#51-powershell-cheat-sheet)
52. [Connection to Lab 5](#52-connection-to-lab-5)

---


# PART A — FOUNDATIONS

## 1. Learning Objectives

By the end of this lab, students will be able to:

1. **Explain** the purpose and basic architecture of PowerShell.
2. **Differentiate** between CMD, Batch scripting, and PowerShell.
3. **Use** common PowerShell cmdlets for file and directory management.
4. **Retrieve** process, service, system, and network information.
5. **Use** variables, pipelines, conditions, and loops in PowerShell.
6. **Create and execute** a simple PowerShell script.
7. **Develop** a basic system-administration automation script.

### Pre-Lab Checklist

Before starting, confirm that you can:

- [ ] Open a terminal window on Windows.
- [ ] Navigate folders with `cd` and list them with `dir` (Lab 2).
- [ ] Create and run a `.bat` file (Lab 3).
- [ ] Open Notepad or VS Code to edit a text file.

---

## 2. Introduction: Why PowerShell?

In the previous labs you interacted with Windows through the **Command Prompt (CMD)** and automated tasks using **Batch scripting**.

Batch scripting is useful, but modern Windows administration often demands more: managing files, processes, services, users, networking, and system configuration — all in a consistent, scriptable way.

This is where **PowerShell** becomes important.

PowerShell is a command-line shell and scripting environment designed for **system administration and automation**. Unlike traditional CMD, PowerShell works heavily with **objects**, not only plain text.

### Objects, Not Just Text

Consider this command:

```powershell
Get-Process
```

It does **not** simply print lines of text. It returns **process objects**, and every object carries *properties* such as:

| Property (concept) | Actual PowerShell property name |
| --- | --- |
| Process name | `ProcessName` |
| Process ID | `Id` |
| CPU time | `CPU` |
| Memory usage | `WorkingSet` |
| Start time | `StartTime` |

This makes PowerShell far more powerful for **filtering, sorting, automation, and administration**, because you can ask questions like *"show me only processes using more than 100 MB"* without parsing any text.

### 🧠 Concept: Text vs Objects

```
CMD (text-based)                     PowerShell (object-based)
-----------------                    --------------------------
tasklist                             Get-Process
   │                                    │
   ▼                                    ▼
Lines of characters                  Objects with named properties
   │                                    │
   ▼                                    ▼
To filter, you must                  To filter, you simply ask
search/parse text                    for a property:  CPU -gt 100
```

---

## 3. What is PowerShell?

### 3.1 Definition

**PowerShell** is a **command-line shell**, **scripting language**, and **automation framework** designed for system administration and configuration management.

It allows administrators and users to:

- Manage files and folders
- Manage processes
- Manage Windows services
- Retrieve system information
- Inspect network configuration
- Automate repetitive tasks
- Work with structured objects
- Create administration scripts

### 3.2 The Three Roles of PowerShell

| Role | What it means | Example |
| --- | --- | --- |
| **Shell** | An interactive prompt where you type commands | `Get-Location` |
| **Scripting language** | A programming language with variables, conditions, loops | `if (...) { ... }` |
| **Automation framework** | Lets you combine commands into repeatable administration tasks | `system_audit.ps1` |

### 3.3 Windows PowerShell vs PowerShell 7

You may see two versions on lab machines:

| Version | Application name | Notes |
| --- | --- | --- |
| **Windows PowerShell 5.1** | "Windows PowerShell" | Built into Windows 10/11. Blue console window by default. |
| **PowerShell 7+** | "PowerShell" (or `pwsh`) | Newer, cross-platform, installed separately. |

> 💡 **Tip:** To see which version you are using, run:
> ```powershell
> $PSVersionTable.PSVersion
> ```

Everything in this lab works in both versions, unless stated otherwise.

---

## 4. PowerShell vs CMD vs Batch

### 4.1 Comparison Table

| Feature | CMD | PowerShell |
| --- | --- | --- |
| **Interface** | Command-line shell | Command-line shell + scripting environment |
| **Typical output** | Mostly text | Objects |
| **Commands** | Traditional commands | Cmdlets + aliases + external commands |
| **Automation** | Batch files | PowerShell scripts |
| **File extension** | `.bat`, `.cmd` | `.ps1` |
| **Pipeline** | Mainly text-based | Object-based |
| **Administration** | Basic / moderate | Advanced |
| **Modern Windows usage** | Supported | Preferred for many administrative tasks |

### 4.2 Example

**CMD:**

```cmd
tasklist
```

**PowerShell:**

```powershell
Get-Process
```

Both display running processes, but PowerShell returns **richer, structured information** that can be filtered, sorted, and reused.

### 4.3 Evolution of the Windows Toolset

```
Windows GUI  →  CMD  →  Batch Scripting  →  PowerShell  →  System Administration
 (click)       (type)   (automate text      (automate      (manage the whole
                         commands)           objects)       system at scale)
```

---

## 5. Cmdlets and the Verb-Noun Pattern

### 5.1 What is a Cmdlet?

A **cmdlet** (pronounced approximately *"command-let"*) is a PowerShell command designed to perform **one specific operation**.

Most cmdlets follow a naming pattern:

```
Verb-Noun
```

Examples:

```powershell
Get-Process
Get-Service
Get-ChildItem
New-Item
Copy-Item
Remove-Item
```

### 5.2 Why Verb-Noun?

The pattern makes commands **easy to understand and easy to guess**.

For example, `Get-Process` means:

- **Get** = retrieve information
- **Process** = about processes

Similarly, `Stop-Process` means:

- **Stop** = terminate
- **Process** = a running process

### 5.3 Common Verbs You Will Meet

| Verb | Meaning | Example |
| --- | --- | --- |
| `Get` | Retrieve / read | `Get-Service` |
| `Set` | Change / replace | `Set-Content` |
| `New` | Create | `New-Item` |
| `Add` | Append | `Add-Content` |
| `Remove` | Delete | `Remove-Item` |
| `Copy` | Duplicate | `Copy-Item` |
| `Move` | Relocate | `Move-Item` |
| `Rename` | Change a name | `Rename-Item` |
| `Start` | Begin | `Start-Process` |
| `Stop` | End | `Stop-Process` |
| `Test` | Check a condition | `Test-Path`, `Test-Connection` |
| `Write` / `Read` | Output / input | `Write-Output`, `Read-Host` |

> 💡 **Tip:** Once you learn the verbs, you can **guess** commands you have never seen. If `Get-Service` lists services, then `Stop-Service` very likely stops one.

---

## 6. Opening PowerShell and Reading the Prompt

### 6.1 Three Ways to Open PowerShell

**Method 1 — Start Menu**

Press the **Windows** key, type `PowerShell`, then open *Windows PowerShell* or *PowerShell*.

**Method 2 — Run Dialog**

1. Press `Win + R`.
2. Type `powershell`.
3. Press **Enter**.

**Method 3 — Windows Terminal**

On modern Windows systems, open **Windows Terminal** and select **PowerShell** from the tab menu.

### 6.2 Understanding the Prompt

A typical prompt looks like:

```
PS C:\Users\Student>
```

| Part | Meaning |
| --- | --- |
| `PS` | Indicates the shell is PowerShell |
| `C:\Users\Student` | Shows the **current location** (working directory) |
| `>` | PowerShell is **ready to receive a command** |

---

## 7. Anatomy of a PowerShell Command

Before writing commands, learn to *read* them. Every PowerShell command is built from the same pieces.

```powershell
New-Item -ItemType Directory -Name "OSLab"
```

| Piece | Name | Role |
| --- | --- | --- |
| `New-Item` | **Cmdlet** | The action to perform |
| `-ItemType` | **Parameter** | A named option (always starts with `-`) |
| `Directory` | **Argument / value** | The value given to that parameter |
| `-Name` | **Parameter** | Another named option |
| `"OSLab"` | **Argument / value** | The value for `-Name` |

```
 Cmdlet         Parameter   Value     Parameter  Value
   │                │          │          │        │
New-Item     -ItemType   Directory     -Name    "OSLab"
```

### Key Rules

1. **Parameters start with a hyphen** (`-Name`, not `Name`).
2. **Cmdlet names are not case-sensitive** — `get-process` and `Get-Process` both work.
3. **Use quotes around values containing spaces** — `"My Folder"`.
4. **Tab completion** — press `Tab` after typing part of a cmdlet or parameter and PowerShell will finish it for you.

> 💡 **Tip:** Press the **Up Arrow** to recall previous commands, and **Tab** to auto-complete. These two habits will save you a large amount of typing.

---

# PART B — LEARNING TO LEARN

## 8. Get-Help — Built-in Documentation

One of the most useful PowerShell commands is:

```powershell
Get-Help
```

### Purpose

Displays help information about PowerShell commands.

### Basic Usage

```powershell
Get-Help Get-Process
```

This provides information about the `Get-Process` cmdlet: its description, syntax, and parameters.

### Detailed Help

```powershell
Get-Help Get-Process -Detailed
```

- `-Detailed` requests **more detailed documentation**, including parameter descriptions.

### Examples Only

```powershell
Get-Help Get-Process -Examples
```

- Displays **practical examples** of how the command can be used.

### Summary of Help Switches

| Command | What you get |
| --- | --- |
| `Get-Help Get-Process` | Basic help |
| `Get-Help Get-Process -Detailed` | Detailed help |
| `Get-Help Get-Process -Examples` | Usage examples only |

> ⚠️ **Note:** On some systems, help files must first be downloaded using `Update-Help` (requires Administrator rights and internet access). If help appears incomplete, ask your instructor before running it.

> 👨‍🏫 **Instructor Tip:** Encourage students to use
> ```powershell
> Get-Help <command> -Examples
> ```
> instead of memorizing every command. A good administrator is not someone who remembers everything — it is someone who knows **how to find answers quickly**.

---

## 9. Get-Command — Discovering Commands

### Command

```powershell
Get-Command
```

### Purpose

Lists the commands available in PowerShell.

The list may include:

- **Cmdlets**
- **Functions**
- **Aliases**
- **Applications**

### Search for a Specific Command

```powershell
Get-Command *process*
```

The asterisk `*` is a **wildcard**. It means: *match any number of characters.*

So this command finds every command whose name **contains** the word `process`.

### More Search Examples

| Command | Finds |
| --- | --- |
| `Get-Command *process*` | Anything containing "process" |
| `Get-Command Get-*` | Every command starting with `Get-` |
| `Get-Command *service*` | Anything related to services |
| `Get-Command -Verb Stop` | Every cmdlet using the verb `Stop` |

### 🧪 Try it

1. Run `Get-Command *service*`. Which cmdlets can *start* or *stop* a service?
2. Use `Get-Help` on one of them with `-Examples`.

This is the real PowerShell workflow: **Discover** (`Get-Command`) → **Learn** (`Get-Help`) → **Use**.

---

## 10. Aliases

An **alias** is a short nickname for a cmdlet. PowerShell includes many aliases so that CMD users feel at home.

| Alias | Real Cmdlet | Notes |
| --- | --- | --- |
| `dir`, `ls`, `gci` | `Get-ChildItem` | List files and folders |
| `cd`, `sl` | `Set-Location` | Change directory |
| `pwd`, `gl` | `Get-Location` | Show current directory |
| `cat`, `type`, `gc` | `Get-Content` | Read a file |
| `copy`, `cp` | `Copy-Item` | Copy |
| `move`, `mv` | `Move-Item` | Move |
| `ren` | `Rename-Item` | Rename |
| `del`, `rm` | `Remove-Item` | Delete |
| `ps`, `gps` | `Get-Process` | List processes |
| `cls`, `clear` | `Clear-Host` | Clear the screen |
| `mkdir` | *(function wrapping `New-Item`)* | Create a folder |

### Find What an Alias Really Is

```powershell
Get-Alias dir
```

### 👨‍🏫 Teaching Point

Students should learn the **real cmdlet names**, even though aliases exist. Reasons:

1. Real names are **self-descriptive** (`Get-ChildItem` explains itself; `gci` does not).
2. Scripts written with full names are **easier to read and maintain**.
3. Aliases can **differ between systems** and operating systems.
4. Professional PowerShell style guides recommend **full names in scripts**.

---

# PART C — FILES AND DIRECTORIES

PowerShell can perform every basic operation you learned in CMD, but using **cmdlets**.

### CMD → PowerShell Mapping

| Task | CMD | PowerShell |
| --- | --- | --- |
| Show current directory | `cd` | `Get-Location` |
| Change directory | `cd folder` | `Set-Location folder` |
| List contents | `dir` | `Get-ChildItem` |
| Create folder | `mkdir` | `New-Item -ItemType Directory` |
| Create file | `echo. > file` | `New-Item -ItemType File` |
| Show file contents | `type file` | `Get-Content file` |
| Copy | `copy` | `Copy-Item` |
| Move | `move` | `Move-Item` |
| Rename | `ren` | `Rename-Item` |
| Delete | `del` | `Remove-Item` |

---

## 11. Navigation: Get-Location, Set-Location, Get-ChildItem

### 11.1 Get-Location

**Command**

```powershell
Get-Location
```

**Purpose:** Displays the current working directory.

**Example output**

```
Path
----
C:\Users\Student
```

**CMD equivalent:** `cd` (with no arguments)

### 11.2 Set-Location

**Command**

```powershell
Set-Location
```

**Purpose:** Changes the current working directory.

**Example**

```powershell
Set-Location Documents
```

**Short alias**

```powershell
cd Documents
```

PowerShell supports `cd` as an alias for convenience.

**Useful variations**

| Command | Result |
| --- | --- |
| `Set-Location ..` | Go up one level |
| `Set-Location \` | Go to the root of the current drive |
| `Set-Location C:\Users` | Go to an absolute path |
| `Set-Location ~` | Go to your home folder |

### 11.3 Get-ChildItem

**Command**

```powershell
Get-ChildItem
```

**Purpose:** Displays files and folders in the current directory.

**Example**

```powershell
Get-ChildItem
```

**Example output**

```
    Directory: C:\Users\Student

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        01/10/2025   09:00 AM                Documents
d-----        01/10/2025   09:05 AM                Downloads
-a----        01/10/2025   10:30 AM           1024 notes.txt
```

- A `Mode` beginning with **`d`** is a **directory** (folder).
- A `Mode` containing **`a`** means the **archive** attribute (a normal file).

**Common alias**

```powershell
dir
```

PowerShell allows `dir` as an alias, but the actual PowerShell cmdlet is `Get-ChildItem`.

**Useful variations**

| Command | Result |
| --- | --- |
| `Get-ChildItem -Recurse` | Include all sub-folders |
| `Get-ChildItem -Filter *.txt` | Show only `.txt` files |
| `Get-ChildItem -Directory` | Show only folders |
| `Get-ChildItem -File` | Show only files |

> 👨‍🏫 **Teaching Point:** Students should learn the real cmdlet names even if aliases exist.

---

## 12. Creating Items: New-Item

### 12.1 Create a Directory

```powershell
New-Item -ItemType Directory -Name "OSLab"
```

**Explanation**

| Part | Meaning |
| --- | --- |
| `New-Item` | Create a new item |
| `-ItemType Directory` | Specify that the item is a **folder** |
| `-Name "OSLab"` | The folder name |

### 12.2 Create a File

```powershell
New-Item -ItemType File -Name "notes.txt"
```

**Result:** creates `notes.txt` in the current directory.

### 12.3 A Simpler Way to Create Folders

PowerShell also provides:

```powershell
mkdir OSLab
```

However, for teaching PowerShell clearly, students should understand:

```powershell
New-Item -ItemType Directory
```

because this demonstrates **proper cmdlet syntax**, which also works for files, registry keys, and other item types.

> ⚠️ **Warning:** `New-Item -ItemType File` fails with an error if the file already exists (unless `-Force` is used, which can **overwrite** it). Use `Test-Path` to check first (see Section 36).

---

## 13. Working with File Content: Set-Content, Add-Content, Get-Content

Three cmdlets handle most text-file work. Understanding the difference between the first two is essential.

### 13.1 Set-Content — Write to a File

```powershell
Set-Content -Path "notes.txt" -Value "Operating Systems Lab"
```

**Purpose:** Writes content to a file, **replacing** any previous content.

| Parameter | Meaning |
| --- | --- |
| `-Path` | File location / name |
| `-Value` | Text to write |

### 13.2 Add-Content — Append to a File

```powershell
Add-Content -Path "notes.txt" -Value "PowerShell Lab"
```

**Purpose:** Adds content **without removing** existing data.

Now the file contains:

```
Operating Systems Lab
PowerShell Lab
```

### 13.3 Get-Content — Read a File

```powershell
Get-Content notes.txt
```

**Purpose:** Displays the contents of a file.

**Expected output**

```
Operating Systems Lab
PowerShell Lab
```

### 13.4 The Key Difference

```
Set-Content   →  OVERWRITE  (old content is lost)
Add-Content   →  APPEND     (old content is kept)
```

| Step | Command | File contains afterward |
| --- | --- | --- |
| 1 | `Set-Content a.txt "One"` | `One` |
| 2 | `Add-Content a.txt "Two"` | `One`, `Two` |
| 3 | `Set-Content a.txt "Three"` | `Three` *(One and Two are gone!)* |

---

## 14. Copy, Move, Rename and Remove

### 14.1 Copy-Item

**Purpose:** Copies files or folders.

**Syntax**

```powershell
Copy-Item -Path <source> -Destination <destination>
```

**Example**

```powershell
Copy-Item -Path "notes.txt" -Destination "Backup"
```

> ⚠️ **Gotcha:** The destination folder **must already exist**. If `Backup` does not exist, PowerShell may create a *file* named `Backup` instead of copying into a folder. Create the folder first, or check with `Test-Path`.

### 14.2 Move-Item

**Purpose:** Moves a file or directory (the original is removed from the old location).

```powershell
Move-Item -Path "notes.txt" -Destination "Documents"
```

### 14.3 Rename-Item

**Purpose:** Renames a file or directory.

```powershell
Rename-Item -Path "notes.txt" -NewName "os_notes.txt"
```

### 14.4 Remove-Item

**Purpose:** Deletes files or directories.

```powershell
Remove-Item "test.txt"
```

> ⚠️ **Warning:** Deletion can be **destructive** and there is **no Recycle Bin** for `Remove-Item` by default. Students should use `Remove-Item` **only in a dedicated practice directory**.

> 💡 **Tip — Preview before you delete:** Add `-WhatIf` to see what *would* happen without actually doing it:
> ```powershell
> Remove-Item "test.txt" -WhatIf
> ```
> Output: `What if: Performing the operation "Remove File" on target "C:\...\test.txt".`
>
> Add `-Confirm` to be asked before each deletion.

### 14.5 Summary Table

| Cmdlet | Action | Original removed? |
| --- | --- | --- |
| `Copy-Item` | Duplicate | No |
| `Move-Item` | Relocate | Yes (moved) |
| `Rename-Item` | Change name | Name changes |
| `Remove-Item` | Delete | Yes |

---

## 15. Practical 1 — Create a Complete Folder Structure

### Objective

Create the following structure:

```
OS_PowerShell
├── Notes
├── Assignments
└── Backup
```

### Commands

```powershell
New-Item -ItemType Directory -Name "OS_PowerShell"
Set-Location "OS_PowerShell"
New-Item -ItemType Directory -Name "Notes"
New-Item -ItemType Directory -Name "Assignments"
New-Item -ItemType Directory -Name "Backup"
```

### Step-by-Step Explanation

| Step | Command | What happens |
| --- | --- | --- |
| 1 | `New-Item ... "OS_PowerShell"` | Creates the main folder |
| 2 | `Set-Location "OS_PowerShell"` | Moves **into** that folder |
| 3 | `New-Item ... "Notes"` | Creates `Notes` **inside** `OS_PowerShell` |
| 4 | `New-Item ... "Assignments"` | Creates `Assignments` |
| 5 | `New-Item ... "Backup"` | Creates `Backup` |

### Verification

```powershell
Get-ChildItem
```

**Expected directories:**

```
Notes
Assignments
Backup
```

---

## 16. Practical 2 — Create and Manage a Text File

### Commands

```powershell
New-Item -ItemType File -Name "lab4.txt"
Set-Content -Path "lab4.txt" -Value "Operating Systems Lab 4"
Add-Content -Path "lab4.txt" -Value "PowerShell Administration"
Get-Content "lab4.txt"
```

### Expected Output

```
Operating Systems Lab 4
PowerShell Administration
```

### What Each Line Does

| Command | Effect |
| --- | --- |
| `New-Item -ItemType File` | Creates an empty file |
| `Set-Content` | Writes the first line (replacing anything inside) |
| `Add-Content` | Appends the second line |
| `Get-Content` | Displays the file to verify |

### 🧪 Try it

Run `Set-Content -Path "lab4.txt" -Value "Oops"` and then `Get-Content "lab4.txt"`. What happened to your original two lines? Why?

---

# PART D — VARIABLES AND INPUT/OUTPUT

## 17. Variables

A **variable** stores data in memory so that it can be used later.

PowerShell variables always begin with:

```
$
```

### Example

```powershell
$name = "Ali"
```

### Explanation

| Part | Meaning |
| --- | --- |
| `$` | Indicates a **variable** |
| `name` | The variable name |
| `=` | **Assignment operator** |
| `"Ali"` | The stored value |

```
   $name   =   "Ali"
     │     │      │
  variable assign  value
   name   operator
```

### Variable Types

PowerShell decides the type automatically:

```powershell
$text   = "Hello"      # String
$number = 42           # Integer
$flag   = $true        # Boolean
$list   = 1, 2, 3      # Array
```

> 💡 **Tip:** To see a variable's type: `$number.GetType().Name`

---

## 18. Write-Output and Read-Host

### 18.1 Displaying a Variable

```powershell
$name = "Ali"
Write-Output $name
```

**Output:**

```
Ali
```

### 18.2 Write-Output

**Command**

```powershell
Write-Output
```

**Purpose:** Sends output to the PowerShell **pipeline** (by default, this appears on screen).

**Example**

```powershell
Write-Output "Operating Systems Lab"
```

**Output**

```
Operating Systems Lab
```

### 18.3 Taking User Input — Read-Host

Use `Read-Host` to ask the user a question and store the answer.

```powershell
$name = Read-Host "Enter your name"
Write-Output "Welcome $name"
```

**Example execution**

```
Enter your name: Hussain
Welcome Hussain
```

> ⚠️ **Important:** `Read-Host` always returns a **string** (text), even if the user types a number. If you need to compare numbers, convert with `[int]` (see Section 31).

---

## 19. String Interpolation

Consider:

```powershell
"Welcome $name"
```

PowerShell **replaces `$name` with its stored value** inside double-quoted strings. This is called **string interpolation** (or variable expansion).

If:

```powershell
$name = "Ahmed"
```

then:

```powershell
Write-Output "Welcome $name"
```

prints:

```
Welcome Ahmed
```

### Double Quotes vs Single Quotes

| Quote type | Behaviour | Example | Output |
| --- | --- | --- | --- |
| Double `"..."` | **Expands** variables | `"Hi $name"` | `Hi Ahmed` |
| Single `'...'` | Treated **literally** | `'Hi $name'` | `Hi $name` |

---

## 20. Practical 3 — Student Information Script

```powershell
# Ask the student for their name
$name = Read-Host "Enter student name"

# Ask for registration number
$reg = Read-Host "Enter registration number"

# Display heading
Write-Output "Student Information"

# Display entered name
Write-Output "Name: $name"

# Display entered registration number
Write-Output "Registration Number: $reg"
```

### Important — Comments

In PowerShell:

```
#
```

starts a **single-line comment**. Everything after `#` on that line is ignored by PowerShell. Good scripts use comments to explain *why* each step exists.

### Sample Run

```
Enter student name: Ali
Enter registration number: BSCS-001
Student Information
Name: Ali
Registration Number: BSCS-001
```

---

# PART E — PROCESSES AND SERVICES

## 21. Processes: Get-Process, Start-Process, Stop-Process

### 🧠 OS Concept

A **process** is an **executing instance of a program**. When you open Notepad, the OS creates a process for it, assigns it a unique **Process ID (PID)**, and allocates memory and CPU time. Process management is one of the core functions of any operating system.

PowerShell provides powerful process-management cmdlets.

### 21.1 Get-Process

**Command**

```powershell
Get-Process
```

**Purpose:** Displays currently running processes.

**Possible properties include:**

| Property | Meaning |
| --- | --- |
| `ProcessName` | Name of the program |
| `Id` | The unique Process ID (PID) |
| `CPU` | Total processor time used, in **seconds** (cumulative — *not* a live percentage) |
| `WorkingSet` | Physical memory currently used, in **bytes** |
| `Handles` | Number of open handles (files, registry keys, etc.) |

**Example output**

```
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    512      28    35124      60212       3.45   4120   1 chrome
    187      12     2840       9876       0.08   7312   1 notepad
```

### 21.2 Find a Specific Process

```powershell
Get-Process notepad
```

- If Notepad is **running**, information about it is displayed.
- If it is **not running**, PowerShell may return an error indicating that the process was not found.

### 21.3 Start-Process

**Command**

```powershell
Start-Process
```

**Purpose:** Starts an application or process.

**Example**

```powershell
Start-Process notepad.exe
```

**Result:** Notepad opens.

### 21.4 Stop-Process

**Command**

```powershell
Stop-Process
```

**Purpose:** Terminates a process.

**Example** — first, confirm it exists:

```powershell
Get-Process notepad
```

Then stop it:

```powershell
Stop-Process -Name notepad
```

> ⚠️ **Warning:** Students should terminate **only safe applications they started themselves**. Stopping system processes can crash Windows or cause data loss.

> 💡 **Tip:** You can also stop a specific process by its PID: `Stop-Process -Id 7312`. This is useful when several processes share the same name.

---

## 22. Practical 4 — Process Management

**Step 1 — Start Notepad**

```powershell
Start-Process notepad.exe
```

**Step 2 — Find it**

```powershell
Get-Process notepad
```

**Step 3 — Observe its PID**

Look at the `Id` column. This number uniquely identifies this running instance.

**Step 4 — Terminate it**

```powershell
Stop-Process -Name notepad
```

**Step 5 (recommended) — Confirm it is gone**

```powershell
Get-Process notepad
```

PowerShell should now report that it cannot find the process.

### Learning Connection

This provides practical exposure to the OS concept of:

> **Process Management** — creating, monitoring, and terminating processes.

```
Start-Process  →  process CREATED  (gets a PID)
Get-Process    →  process MONITORED
Stop-Process   →  process TERMINATED
```

> 💡 **Note:** On some Windows 11 systems, Notepad is a modern app and may leave more than one process. If `Stop-Process -Name notepad` closes only one window, run `Get-Process notepad` again to check.

---

## 23. Windows Services and Get-Service

### 23.1 What is a Service?

A **service** is a program that can run **in the background** to provide operating-system or application functionality — usually with no window and no user interaction.

Examples include services related to:

- Networking
- Printing
- Updates
- Security
- Remote communication

### Process vs Service

| | Process | Service |
| --- | --- | --- |
| **Definition** | Any running program instance | A special background program managed by Windows |
| **Needs a user logged in?** | Usually yes | Not necessarily |
| **Has a window?** | Often | Usually no |
| **Managed with** | `Get-Process` | `Get-Service` |
| **Example** | `notepad` | Print Spooler |

### 23.2 Get-Service

**Command**

```powershell
Get-Service
```

**Purpose:** Displays Windows services.

**Typical information:**

| Column | Meaning |
| --- | --- |
| `Status` | `Running` or `Stopped` |
| `Name` | Short internal name |
| `DisplayName` | Human-friendly name |

**Example output**

```
Status   Name               DisplayName
------   ----               -----------
Running  Spooler            Print Spooler
Stopped  XblAuthManager     Xbox Live Auth Manager
Running  Dnscache           DNS Client
```

### 23.3 Find Running Services

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

This introduces an important PowerShell feature: the **Pipeline** — explained next.

---

# PART F — THE PIPELINE

## 24. The Pipeline

The pipe symbol is:

```
|
```

In PowerShell, the pipeline sends **objects** from one command to the next.

### Example

```powershell
Get-Process | Sort-Object CPU
```

### Flow

```
Get-Process
      ↓
Process Objects
      ↓
Sort-Object CPU
      ↓
Sorted Results
```

### 🧠 Concept: The Assembly Line

Think of the pipeline as a **factory assembly line**:

```
 [ Get-Process ]──►[ Where-Object ]──►[ Sort-Object ]──►[ Select-Object ]──► Screen
   produces          keeps only         arranges           keeps only the
   all objects       matching ones      them in order      needed columns
```

Each station receives **complete objects** (with all their properties), does one job, and passes them on. This is why PowerShell commands combine so powerfully.

### Line Continuation

A pipeline can be spread over several lines by ending each line with `|`:

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5
```

This is purely for readability; PowerShell treats it as one command.

### 💡 Peeking Inside an Object: Get-Member

To discover what properties an object has, pipe it to `Get-Member`:

```powershell
Get-Process | Get-Member
```

This lists every **property** and **method** available — and tells you which names you can use with `Sort-Object`, `Where-Object`, and `Select-Object`.

---

## 25. Where-Object and Comparison Operators

### 25.1 Where-Object

**Purpose:** Filters objects according to a condition.

**Example**

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

### Explanation, Piece by Piece

| Piece | Meaning |
| --- | --- |
| `Get-Service` | Retrieves all services |
| `\|` | Sends the service objects to the next command |
| `Where-Object` | Filters them |
| `{ ... }` | The **filter block** (a small piece of code run for each object) |
| `$_` | Represents **the current object** being processed |
| `.Status` | Accesses the object's `Status` property |
| `-eq` | Means *equal to* |
| `"Running"` | The required value |

```
Get-Service | Where-Object { $_.Status -eq "Running" }
                              │  │       │       │
                              │  │       │       └─ value to match
                              │  │       └───────── operator (equals)
                              │  └───────────────── property of the object
                              └──────────────────── "the current object"
```

### 25.2 PowerShell Comparison Operators

PowerShell does **not** use `>`, `<`, or `==` for comparisons (those have other meanings). It uses **letter-based operators**:

| Operator | Meaning |
| --- | --- |
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |
| `-lt` | Less than |
| `-le` | Less than or equal |

**Example**

```powershell
$marks -ge 50
```

means: *Marks are greater than or equal to 50.*

### More Filter Examples

```powershell
# Processes using more than 100 seconds of CPU time
Get-Process | Where-Object {$_.CPU -gt 100}

# Services that are stopped
Get-Service | Where-Object {$_.Status -eq "Stopped"}

# Processes NOT named chrome
Get-Process | Where-Object {$_.ProcessName -ne "chrome"}
```

> ⚠️ **Warning:** Using `>` in PowerShell **redirects output to a file** — it does not compare values. Always use `-gt`, `-lt`, etc.

---

## 26. Sort-Object and Select-Object

### 26.1 Sorting Data

Use:

```powershell
Sort-Object
```

**Example**

```powershell
Get-Process | Sort-Object CPU
```

This sorts processes according to CPU time, lowest first (ascending).

### 26.2 Descending Sort

```powershell
Get-Process | Sort-Object CPU -Descending
```

`-Descending` sorts from **higher to lower** values — so the busiest processes appear first.

### 26.3 Showing Selected Properties

Use:

```powershell
Select-Object
```

**Example**

```powershell
Get-Process | Select-Object ProcessName, Id
```

**Purpose:** Shows **only** the selected properties. This is much cleaner than displaying every available property.

### 26.4 Selecting a Number of Items

```powershell
Get-Process | Select-Object -First 5
```

| Parameter | Effect |
| --- | --- |
| `-First 5` | Keep only the first 5 results |
| `-Last 5` | Keep only the last 5 results |

---

## 27. A Powerful Pipeline Example

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5 ProcessName, Id, CPU
```

### Meaning

| Stage | Action |
| --- | --- |
| 1 | Retrieve processes. |
| 2 | Sort them by CPU time. |
| 3 | Highest first (`-Descending`). |
| 4 | Select the top five. |
| 5 | Display process name, PID, and CPU information. |

```
Get-Process ─► Sort-Object CPU -Descending ─► Select-Object -First 5 ProcessName, Id, CPU
 (all objects)      (busiest first)                  (top 5, 3 columns only)
```

This is a **realistic administration task** — it answers the question *"What is using my computer's processor the most?"*

### Pattern to Remember

> **Retrieve → Filter / Sort → Select → Automate**

---

# PART G — SYSTEM AND NETWORK INFORMATION

## 28. System Information: Get-ComputerInfo

### Command

```powershell
Get-ComputerInfo
```

### Purpose

Displays detailed information about the computer and operating system.

It may include:

- Windows version
- OS architecture
- Computer name
- BIOS information
- Windows installation details
- Hardware information

### Selecting Specific Properties

Because the output is **extensive** (over a hundred properties), students should select only the useful ones:

```powershell
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName
```

| Property | Meaning |
| --- | --- |
| `WindowsProductName` | Edition, e.g. *Windows 11 Pro* |
| `WindowsVersion` | Version number, e.g. *23H2* |
| `OsArchitecture` | `64-bit` or `32-bit` |
| `CsName` | Computer name |

**Result:** a clean, readable system-information report.

> 💡 **Note:** `Get-ComputerInfo` can take a few seconds to run. This is normal.

---

## 29. Network Information

On modern Windows systems, PowerShell provides dedicated networking cmdlets.

### 29.1 Get-NetIPAddress

```powershell
Get-NetIPAddress
```

**Purpose:** Displays IP addresses configured on network interfaces.

To focus on IPv4:

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

- `-AddressFamily IPv4` limits the output to **IPv4** addresses.

### 29.2 Get-NetAdapter

```powershell
Get-NetAdapter
```

**Purpose:** Displays network adapters and their status.

**Typical fields:**

| Field | Meaning |
| --- | --- |
| `Name` | Adapter name (e.g., Wi-Fi, Ethernet) |
| `InterfaceDescription` | Hardware description |
| `Status` | `Up` or `Disconnected` |
| `MacAddress` | Physical (hardware) address |
| `LinkSpeed` | Connection speed |

### 29.3 Test-Connection — Test Connectivity

PowerShell provides:

```powershell
Test-Connection
```

**Example**

```powershell
Test-Connection 127.0.0.1
```

This performs a connectivity test similar in purpose to `ping`.

**Another example**

```powershell
Test-Connection google.com -Count 2
```

- `-Count 2` requests **two** echo tests instead of the default number.

> 💡 **Note:** `127.0.0.1` is the **loopback address** — it tests your own computer's network stack and works even without internet. Testing `google.com` requires an active internet connection and a network that allows it.

### CMD → PowerShell (Network)

| CMD | PowerShell |
| --- | --- |
| `ipconfig` | `Get-NetIPAddress` |
| `ping` | `Test-Connection` |

---

## 30. Practical 5 — Basic System Audit

Run each block in turn.

**1. System information**

```powershell
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName
```

**2. First five processes**

```powershell
Get-Process |
    Select-Object -First 5 ProcessName, Id
```

**3. First five running services**

```powershell
Get-Service |
    Where-Object {$_.Status -eq "Running"} |
    Select-Object -First 5
```

**4. IPv4 addresses**

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

### Result

Students now have a **basic system-administration report** covering:

| Area | Cmdlet used |
| --- | --- |
| System | `Get-ComputerInfo` |
| Processes | `Get-Process` |
| Services | `Get-Service` |
| Network | `Get-NetIPAddress` |

---

# PART H — CONTROL FLOW

## 31. If / Else: Decision Making

### 31.1 IF Statement

**Syntax**

```powershell
if (condition) {
    commands
}
```

**Example**

```powershell
$marks = 70

if ($marks -ge 50) {
    Write-Output "PASS"
}
```

**Output:** `PASS`

### 31.2 IF / ELSE

```powershell
$marks = Read-Host "Enter marks"

if ([int]$marks -ge 50) {
    Write-Output "PASS"
}
else {
    Write-Output "FAIL"
}
```

### Why `[int]`?

`[int]` **converts** the entered value to an integer for numeric comparison.

`Read-Host` returns **text**. Without conversion, PowerShell might compare the values as *strings* (alphabetical order), which can give wrong results — for example, text `"9"` is "greater than" text `"50"` alphabetically.

### 31.3 Flow of an If/Else

```
        ┌───────────────┐
        │ Is marks ≥ 50?│
        └───────┬───────┘
         Yes ┌──┴──┐ No
             ▼     ▼
          "PASS"  "FAIL"
```

### 31.4 Adding Multiple Conditions: elseif

```powershell
if ($marks -ge 80) {
    Write-Output "Grade A"
}
elseif ($marks -ge 50) {
    Write-Output "Grade B"
}
else {
    Write-Output "FAIL"
}
```

---

## 32. Practical 6 — Administrator Check Scenario

For teaching conditions, consider a simple **system-state check**:

```powershell
$process = Get-Process notepad -ErrorAction SilentlyContinue

if ($process) {
    Write-Output "Notepad is running."
}
else {
    Write-Output "Notepad is not running."
}
```

### How It Works

| Line | Explanation |
| --- | --- |
| `$process = Get-Process notepad ...` | Stores the result of the search in a variable. If found, `$process` holds the process object; if not, it is empty. |
| `if ($process)` | An object that exists counts as **true**; empty (`$null`) counts as **false**. |
| `-ErrorAction SilentlyContinue` | Prevents the normal *"process not found"* error from cluttering the screen. |

### 🧪 Try it

1. Run the script **without** Notepad open → what is printed?
2. Run `Start-Process notepad.exe`, then run the script again → what changes?

This is a miniature version of how real monitoring scripts **check system state and react**.

---

## 33. Loops: for and foreach

PowerShell supports several loop structures. Loops let you **repeat actions** without retyping commands.

### 33.1 The `for` Loop

```powershell
for ($i = 1; $i -le 5; $i++) {
    Write-Output $i
}
```

**Output**

```
1
2
3
4
5
```

**Explanation**

| Part | Meaning |
| --- | --- |
| `$i = 1` | **Initial value** — the loop starts at 1 |
| `$i -le 5` | **Condition** — continue while `i` is less than or equal to 5 |
| `$i++` | **Update** — increase `i` by 1 after every iteration |

```
 start: i=1 ──► check i≤5? ──yes──► run body ──► i++ ──┐
                    ▲                                    │
                    └────────────────────────────────────┘
                    │no
                    ▼
                  finish
```

### 33.2 Create Multiple Folders Automatically

```powershell
for ($i = 1; $i -le 10; $i++) {
    New-Item -ItemType Directory -Name "Lab$i"
}
```

**Creates:**

```
Lab1
Lab2
Lab3
...
Lab10
```

Ten folders from three lines of code. Doing this by hand would take ten separate commands — this is the essence of **automation**.

### 33.3 The `foreach` Loop

PowerShell also provides:

```powershell
foreach
```

**Example**

```powershell
$folders = "Theory", "Lab", "Assignment"

foreach ($folder in $folders) {
    New-Item -ItemType Directory -Name $folder
}
```

**Explanation**

| Part | Meaning |
| --- | --- |
| `$folders` | Stores **multiple** folder names (an array) |
| `$folder` | Represents **one** folder name during each loop iteration |

```
Iteration 1:  $folder = "Theory"      → creates Theory
Iteration 2:  $folder = "Lab"         → creates Lab
Iteration 3:  $folder = "Assignment"  → creates Assignment
```

### When to Use Which

| Loop | Best for |
| --- | --- |
| `for` | Repeating a task a **known number of times** |
| `foreach` | Doing something **for each item** in a collection |

> ⚠️ **Note:** Running the loop examples twice in the same folder will produce "already exists" errors. Delete the practice folders or run them in a fresh directory.

---

# PART I — SCRIPTING AND AUTOMATION

## 34. PowerShell Scripts (.ps1)

A **script** is a text file containing PowerShell commands that run **in order**, saved so you can reuse it.

PowerShell scripts normally use the extension:

```
.ps1
```

Example filename:

```
lab4.ps1
```

### 34.1 First PowerShell Script

Create a file named:

```
hello.ps1
```

with this content:

```powershell
# Display a welcome message
Write-Output "Welcome to Operating Systems Lab"

# Ask for student name
$name = Read-Host "Enter your name"

# Display personalized message
Write-Output "Welcome $name"

# Keep the window open
Read-Host "Press Enter to exit"
```

### 34.2 How to Create the File

**Option A — Notepad**
1. Open Notepad.
2. Type the script.
3. *File → Save As* → name it `hello.ps1` → set **Save as type** to *All Files* (otherwise Notepad saves `hello.ps1.txt`).

**Option B — VS Code**
1. Create a new file and save it as `hello.ps1`.
2. VS Code recognizes it as PowerShell and applies syntax colouring.

**Option C — PowerShell itself**

```powershell
New-Item -ItemType File -Name "hello.ps1"
notepad hello.ps1
```

### 34.3 How to Run the Script

Navigate to the folder containing the script, then run:

```powershell
.\hello.ps1
```

> 💡 **Why the `.\`?** `.` means *"the current folder"*. For safety, PowerShell does not run scripts from the current folder unless you say so explicitly. Typing just `hello.ps1` will fail.

---

## 35. Running Scripts and Execution Policy

Depending on Windows configuration, PowerShell may **restrict script execution**.

To inspect the current policy:

```powershell
Get-ExecutionPolicy
```

### Possible Outputs

| Policy | Meaning |
| --- | --- |
| `Restricted` | No scripts may run (interactive commands still work). Default on many Windows client systems. |
| `RemoteSigned` | Local scripts run; scripts downloaded from the internet must be digitally signed. |
| `AllSigned` | All scripts must be digitally signed by a trusted publisher. |
| `Bypass` | Nothing is blocked; no warnings. |

### Typical Error When Blocked

```
.\hello.ps1 : File C:\...\hello.ps1 cannot be loaded because running scripts is
disabled on this system.
```

### Important

Execution policy is a **PowerShell safety feature**, **not a complete security boundary**. It exists mainly to prevent *accidental* execution of untrusted scripts.

Students should **not change organizational security policies without instructor or administrator permission**.

For institutional labs, the **instructor should configure an appropriate approved environment in advance**.

### 👨‍🏫 Instructor Reference (Only When Approved)

If the lab policy permits, a narrow, temporary option is to relax the policy for **the current PowerShell window only**:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

- `-Scope Process` affects only the current window and reverts when it is closed.
- This avoids changing machine-wide or user-wide settings.

---

## 36. Test-Path and Out-File

### 36.1 Test-Path

**Command**

```powershell
Test-Path
```

**Purpose:** Checks whether a file or directory **exists**.

**Example**

```powershell
Test-Path "student.txt"
```

**Possible output**

```
True
```

or

```
False
```

**Why it matters:** scripts should **check before acting**, to avoid errors such as "folder already exists".

### The `!` (NOT) Operator

`!` means **logical NOT** — it reverses true/false.

```powershell
if (!(Test-Path "Backup")) {
    New-Item -ItemType Directory -Name "Backup"
}
```

Read aloud: *"If the Backup folder does **not** exist, create it."*

| `Test-Path "Backup"` | `!(Test-Path "Backup")` | Action |
| --- | --- | --- |
| `True` (exists) | `False` | Skip creation |
| `False` (missing) | `True` | Create folder |

### 36.2 Out-File

**Command**

```powershell
Out-File
```

**Purpose:** Sends command output to a file.

**Example**

```powershell
Get-Process | Out-File processes.txt
```

**Flow**

```
Get-Process
     ↓
Process Objects
     ↓
Pipeline
     ↓
Out-File
     ↓
processes.txt
```

> 💡 **Difference from `Set-Content`:** `Set-Content` writes *text you provide*; `Out-File` writes *whatever a command displays*, formatted as it would appear on screen.

---

## 37. Practical 7 — Student Record Automation

```powershell
# Ask for student information
$name = Read-Host "Enter student name"
$reg  = Read-Host "Enter registration number"

# Create main directory
New-Item -ItemType Directory -Name $reg -ErrorAction SilentlyContinue

# Move into student directory
Set-Location $reg

# Create student record
Set-Content -Path "student.txt" -Value "Name: $name"

# Add registration number
Add-Content -Path "student.txt" -Value "Registration: $reg"

# Create Backup directory if missing
if (!(Test-Path "Backup")) {
    New-Item -ItemType Directory -Name "Backup"
}

# Copy record into Backup
Copy-Item -Path "student.txt" -Destination "Backup"

# Display saved record
Get-Content "student.txt"

Write-Output "Student record created successfully."
```

### Walkthrough

| Step | What it does | Concepts used |
| --- | --- | --- |
| 1 | Reads name and registration number | `Read-Host`, variables |
| 2 | Creates a folder named after the registration number | `New-Item`, `-ErrorAction` |
| 3 | Moves into that folder | `Set-Location` |
| 4 | Writes the name to `student.txt` | `Set-Content` |
| 5 | Appends the registration number | `Add-Content` |
| 6 | Creates `Backup` only if missing | `Test-Path`, `if`, `!` |
| 7 | Copies the file into `Backup` | `Copy-Item` |
| 8 | Shows the record and a success message | `Get-Content`, `Write-Output` |

### Expected Result

```
Name: Ali
Registration: BSCS-001
Student record created successfully.
```

Resulting structure:

```
BSCS-001
├── student.txt
└── Backup
    └── student.txt
```

---

## 38. Complete Automation Example: System Report

### Scenario

An IT administrator needs a script that:

1. Creates a system-report folder.
2. Saves computer information.
3. Saves running-process information.
4. Saves running-service information.
5. Creates a backup copy.

### Script

```powershell
# Define the report directory
$reportFolder = "System_Report"

# Create report directory if it does not exist
if (!(Test-Path $reportFolder)) {
    New-Item -ItemType Directory -Name $reportFolder
}

# Save basic computer information
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName |
    Out-File "$reportFolder\computer.txt"

# Save process information
Get-Process |
    Select-Object ProcessName, Id |
    Out-File "$reportFolder\processes.txt"

# Save running services
Get-Service |
    Where-Object {$_.Status -eq "Running"} |
    Out-File "$reportFolder\services.txt"

# Display completion message
Write-Output "System report generated successfully."
```

### Why Use a Variable for the Folder Name?

`$reportFolder` is defined **once** at the top and reused. If you later want to rename the folder, you change **one line** instead of four. This is a basic principle of maintainable scripts.

### Resulting Output

```
System_Report
├── computer.txt
├── processes.txt
└── services.txt
```

> 💡 **Note:** The script above does not yet create the backup copy listed in the scenario. Extending it with a `Backup` folder and `Copy-Item` is exactly what you will practice in Section 41.

---

# PART J — APPLIED PRACTICE

## 39. Worked Examples

### 39.1 Basic Worked Example

**Problem:** Create a folder called `PowerShellLab` and display it.

**Solution**

```powershell
New-Item -ItemType Directory -Name "PowerShellLab"
Get-ChildItem
```

**Explanation**

- `New-Item` creates the folder.
- `Get-ChildItem` verifies that it exists.

---

### 39.2 Intermediate Worked Example

**Problem:** Create a file called `student.txt`, write a student's name into it, add their registration number, and display the contents.

**Solution**

```powershell
Set-Content -Path "student.txt" -Value "Name: Ali"
Add-Content -Path "student.txt" -Value "Registration: BSCS-001"
Get-Content "student.txt"
```

**Expected Output**

```
Name: Ali
Registration: BSCS-001
```

**Explanation**

`Set-Content` creates the file (if it does not exist) and writes the first line. `Add-Content` appends the second line without erasing the first. `Get-Content` displays the result.

---

### 39.3 Real-World Problem-Based Example

**Scenario:** A user reports that their computer is **slow**. As a junior system administrator, you are asked to identify:

- System information
- Processes using CPU
- Running services
- Network configuration

**Solution**

*Check the system:*

```powershell
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture
```

*Check CPU-consuming processes:*

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5 ProcessName, Id, CPU
```

*Check running services:*

```powershell
Get-Service |
    Where-Object {$_.Status -eq "Running"}
```

*Check network addresses:*

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

**Reasoning**

Each cmdlet gives **evidence about a different part of system operation**:

| Question | Cmdlet | What it reveals |
| --- | --- | --- |
| What system is this? | `Get-ComputerInfo` | OS version, architecture, whether it is under-powered |
| What is using the processor? | `Get-Process` + sort | Runaway or heavy applications |
| What background work is running? | `Get-Service` | Unexpected or unnecessary services |
| Is the network configured? | `Get-NetIPAddress` | Network-related slowness |

This is the **diagnostic thinking** of a system administrator: *gather evidence first, then decide.*

---

## 40. Practical Questions with Solutions

> Try each question **yourself first**, then compare with the solution.

### Question 1 — Basic

Display the current directory.

**Solution**

```powershell
Get-Location
```

---

### Question 2 — Basic

Display all files and directories.

**Solution**

```powershell
Get-ChildItem
```

---

### Question 3 — Intermediate

Create a folder named `OS_Assignment`.

**Solution**

```powershell
New-Item -ItemType Directory -Name "OS_Assignment"
```

---

### Question 4 — Intermediate

Display all running processes and show only the process name and PID.

**Solution**

```powershell
Get-Process |
    Select-Object ProcessName, Id
```

---

### Question 5 — Problem Solving

Display only the first five running services.

**Solution**

```powershell
Get-Service |
    Where-Object {$_.Status -eq "Running"} |
    Select-Object -First 5
```

---

## 41. Student Hands-On Activity — IT System Audit

### Scenario

You are working as a **junior Windows administrator**.

Create a PowerShell script named:

```
system_audit.ps1
```

### Requirements

The script must:

- [ ] Create a folder named `System_Audit`.
- [ ] Record basic Windows/system information.
- [ ] Record running processes.
- [ ] Record running services.
- [ ] Record IPv4 addresses.
- [ ] Create a `Backup` folder.
- [ ] Copy all report files to `Backup`.
- [ ] Display: `System Audit Completed Successfully`
- [ ] Verify that the `Backup` directory exists.

### Expected Final Structure

```
System_Audit
├── computer_info.txt
├── processes.txt
├── services.txt
├── network.txt
└── Backup
    ├── computer_info.txt
    ├── processes.txt
    ├── services.txt
    └── network.txt
```

### Suggested Approach

1. **Plan first** — list each requirement and the cmdlet you will use.
2. Build and test **one step at a time** in the console.
3. Move working commands into the `.ps1` file.
4. Run the full script and verify the structure with `Get-ChildItem -Recurse`.

> 💡 Try it on your own before looking at the instructor solution below.

---

## 42. Instructor Solution and Line-by-Line Explanation

### 42.1 Instructor Solution

```powershell
# Create main audit directory if it does not exist
if (!(Test-Path "System_Audit")) {
    New-Item -ItemType Directory -Name "System_Audit"
}

# Move into audit directory
Set-Location "System_Audit"

# Save basic computer information
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName |
    Out-File "computer_info.txt"

# Save process information
Get-Process |
    Select-Object ProcessName, Id |
    Out-File "processes.txt"

# Save running services
Get-Service |
    Where-Object {$_.Status -eq "Running"} |
    Out-File "services.txt"

# Save IPv4 network information
Get-NetIPAddress -AddressFamily IPv4 |
    Out-File "network.txt"

# Create Backup directory if it does not already exist
if (!(Test-Path "Backup")) {
    New-Item -ItemType Directory -Name "Backup"
}

# Copy all generated text reports to Backup
Copy-Item -Path "*.txt" -Destination "Backup"

# Verify backup directory
if (Test-Path "Backup") {
    Write-Output "System Audit Completed Successfully"
}
```

### 42.2 Line-by-Line Explanation of Important Parts

**Check-before-create**

```powershell
if (!(Test-Path "System_Audit"))
```

- `Test-Path` checks whether the directory exists.
- `!` means **logical NOT**.
- Therefore: *"If `System_Audit` does NOT exist..."*

**Collect system information**

```powershell
Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName
```

Retrieves computer information and selects **only the required properties**.

**Collect process information**

```powershell
Get-Process |
    Select-Object ProcessName, Id
```

Retrieves process objects and selects **process names and IDs**.

**Collect running services**

```powershell
Get-Service |
    Where-Object {$_.Status -eq "Running"}
```

Retrieves services and keeps **only those whose status is `Running`**.

**Copy reports**

```powershell
Copy-Item -Path "*.txt" -Destination "Backup"
```

Copies **every `.txt` file** in the current directory into `Backup`. The wildcard `*` matches any filename.

### 42.3 Understanding the Script as a Whole

```
Check/Create folder ─► Enter folder ─► Collect 4 reports ─► Create Backup ─► Copy reports ─► Verify
   Test-Path            Set-Location     Out-File ×4         New-Item        Copy-Item      Test-Path
```

### 42.4 A Stronger Verification (Discussion Point)

The final check above confirms only that the `Backup` **folder** exists. A more thorough administrator would confirm that the **files were actually copied**:

```powershell
Get-ChildItem "Backup"
```

> 👨‍🏫 **Discussion question for students:** *"Does `Test-Path "Backup"` prove that the copy succeeded? What could go wrong even when the folder exists?"*

---

# PART K — QUALITY, SAFETY AND ASSESSMENT

## 43. Common Student Mistakes

### Mistake 1 — Forgetting `$` Before Variable Names

❌ **Incorrect**

```powershell
name = "Ali"
```

✅ **Correct**

```powershell
$name = "Ali"
```

---

### Mistake 2 — Confusing CMD Commands With PowerShell Cmdlets

Students may use:

```powershell
tasklist
```

PowerShell can execute many traditional external commands, but the **native PowerShell approach** is:

```powershell
Get-Process
```

The native cmdlet returns **objects**, so it works with `Where-Object`, `Sort-Object`, and `Select-Object`; the old command returns plain text.

---

### Mistake 3 — Confusing `Set-Content` and `Add-Content`

```
Set-Content  replaces content.
Add-Content  appends content.
```

---

### Mistake 4 — Removing Important Files

❌ **Incorrect lab practice**

```powershell
Remove-Item C:\Windows\...
```

**Never experiment inside protected Windows directories.**

---

### Mistake 5 — Stopping Unknown Services

Do not randomly use:

```powershell
Stop-Service
```

Windows services may be required for **network, security, updates, or other important functionality**.

---

### Additional Frequent Mistakes

| Mistake | Wrong | Right |
| --- | --- | --- |
| Using `>` to compare | `$x > 5` | `$x -gt 5` |
| Forgetting `.\` to run a script | `hello.ps1` | `.\hello.ps1` |
| Spaces in names without quotes | `New-Item -Name My Folder` | `New-Item -Name "My Folder"` |
| Comparing `Read-Host` as a number without `[int]` | `$m -ge 50` | `[int]$m -ge 50` |
| Missing destination folder in `Copy-Item` | Copy to a non-existent folder | Create folder first |
| Saving script as `.txt` | `hello.ps1.txt` | `hello.ps1` |

---

## 44. Troubleshooting Guide

| Symptom / Error | Likely Cause | Fix |
| --- | --- | --- |
| *"running scripts is disabled on this system"* | Execution policy is `Restricted` | Ask the instructor; see Section 35 |
| *"The term 'xyz' is not recognized as the name of a cmdlet"* | Typo, or wrong command name | Check spelling; use `Get-Command *xyz*` |
| *"Cannot find a process with the name 'notepad'"* | Process is not running | Start it first, or use `-ErrorAction SilentlyContinue` |
| *"An item with the specified name already exists"* | Folder or file already created | Use `Test-Path` before creating |
| *"Cannot find path ... because it does not exist"* | Wrong path or typo | Run `Get-Location` and `Get-ChildItem` to check where you are |
| Variable prints nothing | Missing `$`, or variable never assigned | Check spelling and assignment |
| `Get-NetIPAddress` is not recognized | Very old Windows or non-Windows system | Use `ipconfig` as an alternative |
| `Test-Connection` times out | No internet or firewall blocks it | Test `127.0.0.1` first |
| Script file will not run from Notepad | Saved as `.ps1.txt` | Re-save with *All Files* type |

### General Debugging Strategy

1. **Read the error message** — PowerShell errors tell you the line and the problem.
2. **Run each line separately** in the console.
3. **Print variables** with `Write-Output $variable` to see what they contain.
4. **Check your location** with `Get-Location`.
5. **Use `Get-Help`** for the cmdlet involved.

---

## 45. Important Safety Notes

PowerShell is **much more powerful** than ordinary CMD and can make **significant system changes**.

Students should:

- ✅ Work inside **dedicated practice directories**.
- ✅ Use `-WhatIf` before destructive commands.
- ✅ Use elevated privileges **only when an activity specifically requires them**.
- ✅ Follow institutional execution-policy settings.
- ❌ Avoid disabling services.
- ❌ Avoid modifying registry settings.
- ❌ Avoid deleting system files.
- ❌ Avoid running unfamiliar scripts.
- ❌ Avoid running everything as Administrator.

> **Principle of least privilege:** always use the *minimum* level of access needed for the job. Running as Administrator all the time means a single mistake — or a malicious script — can damage the entire system.

---

## 46. Instructor Notes

### Suggested Opening Demonstration

A useful way to begin this lecture is by showing students, from CMD:

```cmd
tasklist
```

Then show, in PowerShell:

```powershell
Get-Process
```

Ask:

> *"Both commands display processes. What makes PowerShell more powerful?"*

Then run:

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5 ProcessName, Id, CPU
```

This shows students immediately that PowerShell can:

> **Retrieve → Filter / Sort → Select → Automate**

all inside **one command pipeline**.

### Second Demonstration

Another strong demonstration is:

```powershell
Get-Service |
    Where-Object {$_.Status -eq "Running"} |
    Select-Object -First 10
```

Explain that PowerShell is working with **service objects and their properties**, not merely searching lines of text.

### Teaching Checklist

- [ ] Confirm every machine opens PowerShell and runs `Get-ExecutionPolicy` **before** class.
- [ ] Prepare an approved execution-policy setting in advance (Section 35).
- [ ] Confirm internet access if `Test-Connection google.com` will be demonstrated.
- [ ] Remind students to work in a practice folder, e.g. `C:\Users\<name>\OS_PowerShell`.
- [ ] Warn about `Remove-Item` and `Stop-Process` before students start.
- [ ] Walk around during Practicals 4 and 7 — these are where most errors occur.

### Suggested Questioning Techniques

| Moment | Question to ask |
| --- | --- |
| After `Get-Process` | *"What do you think is inside each result?"* → leads to objects |
| After `Where-Object` | *"What does `$_` represent?"* |
| After Practical 7 | *"What would happen if we ran it twice?"* → leads to `Test-Path` |
| After the Instructor Solution | *"How could we prove the backup actually worked?"* |

---

## 47. Quick Knowledge Check

Test yourself — cover the answers and try first.

| # | Question | Answer |
| --- | --- | --- |
| 1 | What is PowerShell? | A command-line shell, scripting language, and automation environment. |
| 2 | What naming structure do most cmdlets use? | Verb-Noun. |
| 3 | Which command lists processes? | `Get-Process` |
| 4 | Which command lists services? | `Get-Service` |
| 5 | Which cmdlet displays files and folders? | `Get-ChildItem` |
| 6 | How do PowerShell variables begin? | With `$`. |
| 7 | Which symbol represents the pipeline? | `\|` |
| 8 | Which command checks whether a path exists? | `Test-Path` |
| 9 | Which extension is used for PowerShell scripts? | `.ps1` |
| 10 | Which command displays PowerShell help? | `Get-Help` |

---

## 48. Viva Questions

**Q1. What is the major difference between CMD and PowerShell?**
PowerShell provides more advanced scripting and works primarily with **structured objects**, whereas CMD works mostly with plain text.

**Q2. What is a cmdlet?**
A PowerShell command designed to perform a specific operation.

**Q3. Why are cmdlets named Verb-Noun?**
The pattern makes their purpose easier to understand and discover.

**Q4. What does `Get-Process` do?**
Retrieves information about running processes.

**Q5. What is the PowerShell pipeline?**
A mechanism for passing **objects** from one command to another.

**Q6. What does `$_` represent?**
The **current object** being processed within commands such as `Where-Object`.

**Q7. What is `Test-Path` used for?**
To determine whether a file or directory exists.

**Q8. What is the difference between `Set-Content` and `Add-Content`?**
`Set-Content` **replaces** content; `Add-Content` **appends** it.

**Q9. What is a Windows service?**
A background program providing system or application functionality.

**Q10. Why is PowerShell useful for system administration?**
It allows administrators to **retrieve, filter, modify, and automate** system configuration and resources efficiently.

---

## 49. Lab Task / Submission

### Task — Windows Administration Dashboard Script

Create:

```
admin_report.ps1
```

### Your Script Must

1. Ask for **student name** and **registration number**.
2. Create a directory named `Admin_Report`.
3. Create `student.txt` containing the student details.
4. Generate `computer.txt` containing:
   - Windows product name
   - Windows version
   - Architecture
   - Computer name
5. Generate `processes.txt` containing the **first 10 processes**.
6. Generate `services.txt` containing **running services**.
7. Generate `network.txt` containing **IPv4 information**.
8. Create a `Backup` directory.
9. Copy all `.txt` reports into `Backup`.
10. **Verify** the backup.
11. Display:

```
Windows Administration Report Completed
```

### Requirement-to-Cmdlet Planning Guide

Use this table to plan your script. It points to the *concept* needed — the script itself is for you to write.

| Requirement | Concepts / cmdlets to consider | Reference |
| --- | --- | --- |
| Ask for name and registration number | `Read-Host`, variables | §18, §20 |
| Create `Admin_Report` | `New-Item`, `Test-Path`, `if` | §12, §36 |
| `student.txt` with details | `Set-Content`, `Add-Content`, string interpolation | §13, §19 |
| `computer.txt` | `Get-ComputerInfo`, `Select-Object`, `Out-File` | §28, §36 |
| First 10 processes | `Get-Process`, `Select-Object -First` | §26 |
| Running services | `Get-Service`, `Where-Object` | §25 |
| IPv4 information | `Get-NetIPAddress -AddressFamily IPv4` | §29 |
| Backup directory | `New-Item`, `Test-Path` | §36 |
| Copy reports | `Copy-Item` with wildcard `*.txt` | §14, §42 |
| Verify backup | `Test-Path`, optionally `Get-ChildItem` | §36, §42.4 |
| Final message | `Write-Output` | §18 |

> 💡 **Hint:** The Student Record Automation (Practical 7) and the IT System Audit (Section 41) together contain almost every technique you need. Study how they are built, then combine them.

### Submission Requirements

Submit the following:

- [ ] The `.ps1` script
- [ ] **Screenshot** of successful execution
- [ ] The generated **report files**
- [ ] **Screenshot** of the directory structure
- [ ] A short explanation of **at least 10** PowerShell cmdlets/operators used

### Suggested Marking Rubric

| Criterion | Marks |
| --- | --- |
| Script runs without errors | 25 |
| All required files generated with correct content | 25 |
| Backup created and verified | 15 |
| Correct use of variables, conditions, and pipeline | 15 |
| Comments and readable formatting | 10 |
| Explanation of 10 cmdlets/operators | 10 |
| **Total** | **100** |

*(Rubric is a suggested template; instructors may adjust marks as needed.)*

---

# PART L — WRAP-UP

## 50. Lecture Summary

In Lab 4, students moved from basic Windows scripting to a **modern system-administration environment**.

### The Progression

```
CMD
 ↓
Batch Scripting
 ↓
PowerShell Cmdlets
 ↓
Objects
 ↓
Pipeline
 ↓
Filtering
 ↓
Processes & Services
 ↓
System Administration
 ↓
Automation
```

### Skills Gained

| Skill Area | What you can now do |
| --- | --- |
| **Navigation & files** | Create, read, write, copy, move, rename, delete |
| **Variables & I/O** | Store data, ask users for input, build messages |
| **Processes & services** | Inspect and control running programs |
| **Pipeline** | Filter, sort, and select objects |
| **System & network** | Retrieve OS details and IP configuration |
| **Control flow** | Make decisions and repeat actions |
| **Scripting** | Write reusable `.ps1` administration scripts |

### Important Commands Covered

`Get-Help` · `Get-Command` · `Get-Location` · `Set-Location` · `Get-ChildItem` · `New-Item` · `Set-Content` · `Add-Content` · `Get-Content` · `Copy-Item` · `Move-Item` · `Rename-Item` · `Remove-Item` · `Get-Process` · `Start-Process` · `Stop-Process` · `Get-Service` · `Where-Object` · `Sort-Object` · `Select-Object` · `Get-ComputerInfo` · `Get-NetIPAddress` · `Get-NetAdapter` · `Test-Connection` · `Test-Path` · `Out-File` · `Read-Host` · `Write-Output`

### The Key Concept

> **PowerShell provides a modern object-based approach to Windows administration and automation, allowing administrators to combine commands into powerful pipelines and reusable scripts.**

---

## 51. PowerShell Cheat Sheet

| Command | Purpose | Example |
| --- | --- | --- |
| `Get-Help` | Command help | `Get-Help Get-Process -Examples` |
| `Get-Command` | Find PowerShell commands | `Get-Command *service*` |
| `Get-Location` | Current directory | `Get-Location` |
| `Set-Location` | Change directory | `Set-Location Documents` |
| `Get-ChildItem` | List files/folders | `Get-ChildItem` |
| `New-Item` | Create item | `New-Item -ItemType Directory -Name Lab` |
| `Set-Content` | Write/replace file content | `Set-Content a.txt "Hello"` |
| `Add-Content` | Append to file | `Add-Content a.txt "New"` |
| `Get-Content` | Read file | `Get-Content a.txt` |
| `Copy-Item` | Copy file/folder | `Copy-Item a.txt Backup` |
| `Move-Item` | Move file/folder | `Move-Item a.txt Docs` |
| `Rename-Item` | Rename item | `Rename-Item a.txt b.txt` |
| `Remove-Item` | Delete item | `Remove-Item test.txt` |
| `Get-Process` | Running processes | `Get-Process` |
| `Start-Process` | Launch process | `Start-Process notepad.exe` |
| `Stop-Process` | Stop process | `Stop-Process -Name notepad` |
| `Get-Service` | View services | `Get-Service` |
| `Where-Object` | Filter objects | `Where-Object {$_.Status -eq "Running"}` |
| `Sort-Object` | Sort objects | `Sort-Object CPU -Descending` |
| `Select-Object` | Select properties/items | `Select-Object ProcessName,Id` |
| `Get-ComputerInfo` | Computer/OS details | `Get-ComputerInfo` |
| `Get-NetIPAddress` | IP information | `Get-NetIPAddress -AddressFamily IPv4` |
| `Get-NetAdapter` | Network adapters | `Get-NetAdapter` |
| `Test-Connection` | Connectivity test | `Test-Connection 127.0.0.1` |
| `Test-Path` | Check path existence | `Test-Path Backup` |
| `Read-Host` | User input | `$name = Read-Host "Name"` |
| `Write-Output` | Display/send output | `Write-Output "Hello"` |
| `Out-File` | Save output | `Get-Process \| Out-File p.txt` |

### Operators and Symbols Quick Reference

| Symbol | Meaning |
| --- | --- |
| `$` | Start of a variable name |
| `$_` | The current pipeline object |
| `\|` | Pipeline — pass objects to the next command |
| `#` | Comment |
| `*` | Wildcard (matches any characters) |
| `!` | Logical NOT |
| `-eq -ne -gt -ge -lt -le` | Comparison operators |
| `[int]` | Convert to integer |
| `.\` | Current folder (used when running scripts) |

### Pipeline Patterns to Memorize

```powershell
# Top N by some property
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5

# Filter by a condition
Get-Service | Where-Object {$_.Status -eq "Running"}

# Save results to a file
Get-Process | Select-Object ProcessName, Id | Out-File processes.txt

# Create folder only if missing
if (!(Test-Path "Backup")) { New-Item -ItemType Directory -Name "Backup" }
```

---

## 52. Connection to Lab 5

Students have now completed the main Windows progression:

```
Windows GUI
     ↓
    CMD
     ↓
Batch Scripting
     ↓
PowerShell
     ↓
System Administration
```

You can now **inspect, control, and automate** a Windows operating system from the command line. These skills — especially processes, services, files, and scripting — form the practical foundation for the next lab.

---

*End of Lab 04 — PowerShell Commands, Scripting & System Administration*
