# OPERATING SYSTEMS LAB — ASSIGNMENT #1

**BSCS-5B**

**CLO:** __________  |  **PLO:** __________

## Title: Windows System Administration & Task Automation Challenge

## Scenario

You have recently joined an organization as a Junior System Administrator. Your organization has provided you with a new Windows computer that needs to be organized, configured, and partially automated.

Your task is to use Windows features, keyboard shortcuts, Command Prompt (CMD), Batch Scripting, and PowerShell to perform the required system-administration activities.

You must practically perform every task on your own computer and prepare a Lab Assignment Report containing screenshots, commands/scripts, and a short explanation of your work.

## Task 1 — Windows & Keyboard Shortcuts

Demonstrate at least **10 useful Windows keyboard shortcuts** that can improve the productivity of a system administrator.

For each shortcut:

- Write the shortcut keys.
- Explain its purpose in one sentence.
- Practically demonstrate it.
- Add a screenshot where appropriate.

At least **5 shortcuts must involve Windows-key combinations**.

## Task 2 — File & Directory Management Using CMD

Open Command Prompt and create the following directory structure **without using File Explorer**:

```text
OS_Lab_Assignment
│
├── Students
├── Reports
│   ├── Weekly
│   └── Final
├── Backup
└── Scripts
```

After creating the structure:

1. Display the current directory.
2. Display the complete directory structure.
3. Create a text file named `student_info.txt`.
4. Write your Name, Registration Number, Semester, and Section into the file using CMD.
5. Display the content of the file in CMD.
6. Copy the file into the `Backup` folder.
7. Rename the copied file to `student_info_backup.txt`.
8. Display all files and folders using CMD.

**Evidence:** Include screenshots showing the commands and their outputs.

## Task 3 — CMD System Investigation

Imagine that your supervisor asks you to quickly investigate the computer.

Using CMD, find and report:

- Computer name
- Current username
- Windows/IP configuration
- Current IP address
- Network connectivity status
- Running processes
- Current date and time

You must identify suitable CMD commands yourself.

For every command, write:

**Command → Purpose → Output/Screenshot → Short Explanation**

## Task 4 — Batch Script Automation

Your supervisor does not want to execute routine commands manually every day.

Create a batch file named `system_check.bat`.

The script should automatically:

1. Display a welcome message.
2. Display the current username.
3. Display computer name.
4. Display current date and time.
5. Display basic IP/network information.
6. Create a folder named `Daily_Backup` if it does not already exist.
7. Copy `student_info.txt` into the backup folder.
8. Display a successful completion message.
9. Pause before closing.

Run the `.bat` file and provide screenshots showing its execution.

Also explain the important commands used in your batch script.

## Task 5 — PowerShell Administration

Now perform the following operations using PowerShell:

1. Display the current working directory.
2. List files and folders.
3. Create a new folder named `PowerShell_Task`.
4. Create a text file inside it.
5. Write your Name and Registration Number into the file.
6. Read/display the contents of the file through PowerShell.
7. Display currently running processes.
8. Display basic system/computer information.
9. Copy your PowerShell-created file into the `Backup` folder.

Provide screenshots of commands and outputs.

## Task 6 — CMD vs PowerShell Comparison

Write a short comparison of CMD and PowerShell based on your practical experience.

Your comparison should discuss:

- Command style
- Ease of use
- Automation capability
- System administration capability
- Which one you would prefer for advanced Windows administration and why

Keep this section between **150–200 words**.

## Submission Requirements

Submit **ONE PDF report** containing:

**Cover Page → Scenario → Tasks 1–6 → Commands/Scripts → Screenshots → Explanations → Conclusion**

Every screenshot must clearly show the practical work performed by the student.

### Important Instructions

- Perform all tasks practically.
- Screenshots must be your own.
- Your Name/Registration Number should be visible in appropriate practical tasks.
- Do not submit screenshots copied from another student.
- Do not submit only commands without execution evidence.
- The batch script must be submitted as code inside the report.
- Add a short Conclusion describing what you learned from the assignment.

## Suggested Marks Distribution — 20 Marks

| Component | Marks |
|---|---:|
| Windows Shortcuts | 2 |
| CMD File/Directory Management | 4 |
| CMD System Investigation | 3 |
| Batch Script Automation | 5 |
| PowerShell Tasks | 4 |
| Comparison, Report & Presentation | 2 |
| **Total** | **20** |

## Learning Outcome

After completing this assignment, students should be able to practically use Windows utilities, CMD commands, keyboard shortcuts, Batch scripts, and PowerShell for basic operating-system administration and task automation.
