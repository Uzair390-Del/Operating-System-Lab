# Operating Systems Lab — Lab 03

## Batch Scripting & Windows Automation

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6?logo=windows&logoColor=white)
![Tools](https://img.shields.io/badge/Tools-CMD%20%7C%20Notepad-000000?logo=windowsterminal&logoColor=white)
![Duration](https://img.shields.io/badge/Duration-3%20Hours-blue)
![Bloom](https://img.shields.io/badge/Bloom%20Level-C3-orange)

---

## Table of Contents

1. [Lab Information](#1-lab-information)
2. [Learning Objectives](#2-learning-objectives)
3. [Introduction](#3-introduction)
4. [Batch File Fundamentals](#4-batch-file-fundamentals)
5. [Creating Your First Batch File](#5-creating-your-first-batch-file)
6. [Core Script Elements](#6-core-script-elements)
7. [Practical 1–2 — Creating Folders](#7-practical-12--creating-folders)
8. [Creating Files and Output Redirection](#8-creating-files-and-output-redirection)
9. [Variables and User Input](#9-variables-and-user-input)
10. [Arithmetic in Batch](#10-arithmetic-in-batch)
11. [Conditions: IF / ELSE](#11-conditions-if--else)
12. [File Existence Checks](#12-file-existence-checks)
13. [Loops: FOR](#13-loops-for)
14. [Window Customization: title and color](#14-window-customization-title-and-color)
15. [Practical 8 — Complete Batch Automation](#15-practical-8--complete-batch-automation)
16. [Worked Examples](#16-worked-examples)
17. [Practical Questions with Solutions](#17-practical-questions-with-solutions)
18. [Student Hands-On Activity](#18-student-hands-on-activity)
19. [Instructor Solution](#19-instructor-solution)
20. [Common Student Mistakes](#20-common-student-mistakes)
21. [Troubleshooting](#21-troubleshooting)
22. [Important Safety Notes](#22-important-safety-notes)
23. [Instructor Notes](#23-instructor-notes)
24. [Quick Knowledge Check](#24-quick-knowledge-check)
25. [Viva Questions](#25-viva-questions)
26. [Lab Task and Submission](#26-lab-task-and-submission)
27. [Lecture Summary](#27-lecture-summary)
28. [Batch Scripting Cheat Sheet](#28-batch-scripting-cheat-sheet)
29. [Connection to Lab 4](#29-connection-to-lab-4)

---

## 1. Lab Information

| Item | Details |
| --- | --- |
| **Course** | Operating Systems – Lab |
| **Lab No.** | Lab 03 |
| **Title** | Batch Scripting & Windows Automation |
| **Main Platform** | Microsoft Windows 10/11 |
| **Suggested Duration** | 3 Hours |
| **Required Tool** | Command Prompt, Notepad |
| **Prerequisite** | Lab 2: Windows CMD Commands |
| **Main CLO** | CLO-4 — Demonstrate knowledge in applying system software and tools available in modern operating systems |
| **Supporting CLO** | CLO-1 — Understand core OS functions and tools |
| **Relevant PLOs** | PLO-02, PLO-05 |
| **Bloom Level** | C3 — Demonstrate / Apply |

---

## 2. Learning Objectives

By the end of this lab, students will be able to:

- **Explain** the purpose of Batch scripting in Windows.
- **Create and execute** `.bat` files.
- **Combine multiple CMD commands** into a single Batch script.
- **Use variables** in Batch scripting.
- **Apply IF/ELSE conditions** in simple automation tasks.
- **Use loops** to repeat operations automatically.
- **Develop** a basic Windows automation script for file and directory management.

---

## 3. Introduction

In the previous lab, students executed Windows CMD commands one at a time. For example:

```bat
mkdir OS_Lab
cd OS_Lab
echo Hello > notes.txt
copy notes.txt Backup
```

If these commands need to be executed repeatedly, typing them manually every time becomes inefficient. A **Batch script** solves this problem.

A Batch script stores a sequence of Windows commands inside a text file with the extension `.bat`. When the file is executed, Windows runs the commands automatically in sequence. For example:

```bat
@echo off
mkdir Backup
copy *.txt Backup
echo Backup completed successfully.
pause
```

Instead of entering four commands separately, the user executes **one file**. This introduces an important concept:

> **Automation means asking the computer to perform repetitive tasks automatically according to predefined instructions.**

---

## 4. Batch File Fundamentals

### 4.1 What is a Batch File?

A **Batch file** is a text file containing one or more commands that are executed sequentially by the Windows command interpreter.

Typical extensions are `.bat` and `.cmd`. For this lab, we mainly use **`.bat`**.

### 4.2 Why Do We Use Batch Scripts?

Batch scripts can be used for:

- Creating folders automatically
- Copying files
- Creating backups
- Renaming files
- Deleting temporary files
- Running programs
- Checking conditions
- Repeating commands
- Displaying messages
- Performing simple administration tasks

### 4.3 Real-World Example

Suppose an employee has to copy all `.txt` files into a Backup folder every evening.

| Manual method | Batch method |
| --- | --- |
| Create Backup folder | One script performs the complete task |
| Find files | |
| Copy files | |
| Check result | |

```bat
@echo off
mkdir Backup
copy *.txt Backup
echo Backup completed.
pause
```

---

## 5. Creating Your First Batch File

| Step | Action |
| --- | --- |
| **1. Open Notepad** | Press `Win + R`, type `notepad`, press **Enter** |
| **2. Write commands** | Type the two lines shown below |
| **3. Save the file** | **File → Save As**, enter `hello.bat`, change **Save as type → All Files**, then save |
| **4. Execute the file** | Double-click `hello.bat` |

**Script**

```bat
echo Hello Students
pause
```

**Expected output**

```text
Hello Students
Press any key to continue . . .
```

### 5.1 Understanding the First Script

| Line | Meaning | Output |
| --- | --- | --- |
| `echo Hello Students` | `echo` displays text on the Command Prompt screen | `Hello Students` |
| `pause` | Stops the script temporarily and waits for the user to press a key | `Press any key to continue . . .` |

**Why is `pause` useful?** Without it, the CMD window may close immediately after the script finishes when launched by double-clicking.

---

## 6. Core Script Elements

### 6.1 `@echo off`

Most Batch scripts start with `@echo off`. It prevents each command itself from being displayed before its output.

**Without `@echo off`**

```bat
echo Hello
pause
```

Possible output:

```text
C:\Lab>echo Hello
Hello

C:\Lab>pause
Press any key to continue . . .
```

**With `@echo off`**

```bat
@echo off
echo Hello
pause
```

Output:

```text
Hello
Press any key to continue . . .
```

This makes the output cleaner.

### 6.2 Meaning of `@`

In `@echo off`, the `@` symbol tells CMD: *do not display this particular command.* Then `echo off` turns command echoing off for the remaining script.

### 6.3 Comments in Batch Files

Comments help programmers explain what the script does. A common method is:

```bat
REM This is a comment
```

`REM` means **Remark** and is ignored during execution.

```bat
@echo off

REM Display welcome message
echo Welcome to OS Lab

pause
```

### 6.4 Basic Batch Script Structure

```bat
@echo off

REM Display heading
echo Operating Systems Lab

REM Create folder
mkdir OS_Lab

REM Display completion message
echo Folder created successfully.

pause
```

### 6.5 Line-by-Line Explanation

| Line | Explanation |
| --- | --- |
| `@echo off` | Hides commands from the output |
| `REM Display heading` | Comment explaining the next instruction |
| `echo Operating Systems Lab` | Displays text |
| `mkdir OS_Lab` | Creates a directory named `OS_Lab` |
| `echo Folder created successfully.` | Displays confirmation |
| `pause` | Waits for keyboard input before closing |

---

## 7. Practical 1–2 — Creating Folders

### Practical 1 — Automatically Create Folders

**Objective:** Create multiple directories automatically using one Batch file.

```bat
@echo off

REM Create main folders
mkdir Lectures
mkdir Assignments
mkdir Backup

echo All folders created successfully.

pause
```

**Expected result:** Three directories are created — `Lectures`, `Assignments`, `Backup`.

### Practical 2 — Create Folder Structure

Create:

```text
Operating_Systems
├── Lectures
├── Assignments
├── Projects
└── Backup
```

**Batch script**

```bat
@echo off

REM Create main directory
mkdir Operating_Systems

REM Enter main directory
cd Operating_Systems

REM Create subdirectories
mkdir Lectures
mkdir Assignments
mkdir Projects
mkdir Backup

REM Display structure
tree

pause
```

**Explanation of `cd`:** `cd Operating_Systems` means **Change Directory**. The script moves into `Operating_Systems` before creating its subfolders.

---

## 8. Creating Files and Output Redirection

### 8.1 Creating Files Through a Batch Script

```bat
@echo off

echo Operating Systems Lab > notes.txt

pause
```

**Result:** Creates `notes.txt` with `Operating Systems Lab` inside it.

### 8.2 Understanding Output Redirection

The symbol `>` redirects command output into a file.

```bat
echo Hello > file.txt
```

This means: *write `Hello` into `file.txt`.*

### 8.3 `>` vs `>>`

| Operator | Purpose | Example |
| --- | --- | --- |
| `>` | Create or overwrite | `echo First Line > notes.txt` |
| `>>` | Append | `echo Second Line >> notes.txt` |

After running both examples, the file contains:

```text
First Line
Second Line
```

### 8.4 Practical 3 — Create a Student Information File

```bat
@echo off

echo Student Name: Ali > student.txt
echo Course: Operating Systems >> student.txt
echo Lab: Batch Scripting >> student.txt

type student.txt

pause
```

**Expected output**

```text
Student Name: Ali
Course: Operating Systems
Lab: Batch Scripting
```

---

## 9. Variables and User Input

### 9.1 Variables

A **variable** stores a value.

**Syntax**

```bat
set variable=value
```

**Example**

```bat
set name=Ali
```

To use the value:

```bat
echo %name%
```

#### Variable Example

```bat
@echo off

REM Store student's name
set name=Ali

REM Display variable
echo Student Name: %name%

pause
```

**Output:** `Student Name: Ali`

### 9.2 Why `%` is Used

In `%name%`, the `%` symbols tell Batch: *retrieve the value stored inside the variable called `name`.*

If `set name=Ahmed`, then `echo %name%` produces `Ahmed`.

### 9.3 Taking Input from the User — `set /p`

```bat
set /p name=Enter your name:
```

| Part | Meaning |
| --- | --- |
| `set` | Create/update variable |
| `/p` | Prompt user for input |
| `name` | Variable name |
| `Enter your name:` | Message shown to user |

### 9.4 Practical 4 — User Input

```bat
@echo off

REM Ask user for name
set /p name=Enter your name: 

REM Display personalized message
echo Welcome %name% to Operating Systems Lab.

pause
```

**Example output**

```text
Enter your name: Hussain
Welcome Hussain to Operating Systems Lab.
```

### 9.5 Multiple Inputs

```bat
@echo off

set /p name=Enter your name: 
set /p reg=Enter registration number: 

echo.
echo Student Information
echo Name: %name%
echo Registration Number: %reg%

pause
```

### 9.6 `echo.` — Blank Line

`echo.` prints an empty line. It makes output easier to read.

---

## 10. Arithmetic in Batch

Batch can perform integer arithmetic using `set /a`.

```bat
set /a result=10+20
echo %result%
```

Output: `30`

### Practical 5 — Simple Addition

```bat
@echo off

REM Take first number
set /p num1=Enter first number: 

REM Take second number
set /p num2=Enter second number: 

REM Add numbers
set /a result=num1+num2

REM Display result
echo Sum = %result%

pause
```

**Explanation**

| Command | Explanation |
| --- | --- |
| `set /p num1=Enter first number:` | Stores user input in `num1` |
| `set /p num2=Enter second number:` | Stores second input |
| `set /a result=num1+num2` | Performs arithmetic addition |
| `echo Sum = %result%` | Displays the result |

---

## 11. Conditions: IF / ELSE

### 11.1 IF Statement

An **IF statement** allows a script to make a decision.

General idea:

```text
IF condition is true
    perform action
```

Basic Batch syntax:

```bat
if condition command
```

### 11.2 String Comparison

```bat
if "%name%"=="Ali" echo Welcome Ali
```

The script checks whether the value of `name` equals `Ali`. If yes, the message is displayed.

### 11.3 IF / ELSE

**Syntax**

```bat
if condition (
    command
) else (
    command
)
```

**Example**

```bat
@echo off

set /p age=Enter your age: 

if %age% GEQ 18 (
    echo Eligible
) else (
    echo Not Eligible
)

pause
```

### 11.4 Comparison Operators

| Operator | Meaning |
| --- | --- |
| `EQU` | Equal |
| `NEQ` | Not Equal |
| `LSS` | Less Than |
| `LEQ` | Less Than or Equal |
| `GTR` | Greater Than |
| `GEQ` | Greater Than or Equal |

Example: `if %marks% GEQ 50` means *if marks are greater than or equal to 50.*

### 11.5 Practical 6 — Pass/Fail Script

```bat
@echo off

REM Ask student marks
set /p marks=Enter marks: 

REM Check result
if %marks% GEQ 50 (
    echo Result: PASS
) else (
    echo Result: FAIL
)

pause
```

---

## 12. File Existence Checks

### 12.1 `IF EXIST`

Batch can check whether a file exists.

**Syntax**

```bat
if exist filename (
    command
)
```

**Example**

```bat
if exist notes.txt echo File exists.
```

### 12.2 `IF EXIST` / `ELSE`

```bat
@echo off

if exist notes.txt (
    echo File found.
) else (
    echo File does not exist.
)

pause
```

This is very useful for automation.

### 12.3 Real-World Example — Backup Only If File Exists

```bat
@echo off

REM Check if file exists
if exist report.txt (

    REM Create backup directory if needed
    if not exist Backup mkdir Backup

    REM Copy file
    copy report.txt Backup

    echo Backup completed.

) else (

    echo Error: report.txt was not found.

)

pause
```

### 12.4 `IF NOT EXIST`

```bat
if not exist Backup mkdir Backup
```

Meaning: if the `Backup` directory does not exist, create it. This avoids unnecessary errors.

---

## 13. Loops: FOR

A loop repeats commands automatically. Batch commonly uses `for`.

### 13.1 Basic FOR Loop

```bat
for %%i in (1 2 3 4 5) do echo %%i
```

Output:

```text
1
2
3
4
5
```

### 13.2 Understanding the Loop

```bat
for %%i in (1 2 3 4 5) do echo %%i
```

| Part | Meaning |
| --- | --- |
| `for` | Starts the loop |
| `%%i` | Loop variable |
| `in` | Specifies the values to iterate through |
| `(1 2 3 4 5)` | Values used by the loop |
| `do` | Specifies what action should be repeated |
| `echo %%i` | Displays the current value |

### 13.3 Practical 7 — Create Multiple Folders Using a Loop

Instead of:

```bat
mkdir Student1
mkdir Student2
mkdir Student3
mkdir Student4
mkdir Student5
```

use:

```bat
@echo off

for %%i in (1 2 3 4 5) do (
    mkdir Student%%i
)

echo Folders created successfully.

pause
```

**Result:** `Student1`, `Student2`, `Student3`, `Student4`, `Student5`

### 13.4 `FOR /L` Loop

For numeric sequences, Batch provides `for /L`.

**Syntax**

```bat
for /L %%i in (start,step,end) do command
```

**Example**

```bat
for /L %%i in (1,1,5) do echo %%i
```

- Start = `1`
- Step = `1`
- End = `5`

Output: `1 2 3 4 5` (one per line)

### 13.5 Create 10 Folders Automatically

```bat
@echo off

for /L %%i in (1,1,10) do (
    mkdir Lab%%i
)

pause
```

Creates `Lab1`, `Lab2`, `Lab3`, ... `Lab10`. This clearly demonstrates the benefit of automation.

---

## 14. Window Customization: title and color

### 14.1 `title`

Batch can change the Command Prompt window title.

```bat
title OS Lab Automation
```

### 14.2 `color`

The `color` command changes the Command Prompt foreground/background colors.

```bat
color 0A
```

- `0` = black background
- `A` = light green foreground

> Use this mainly for demonstration; it is not required for functional automation.

---

## 15. Practical 8 — Complete Batch Automation

**Objective:** Create a script that automatically:

- Displays a title
- Accepts student name
- Creates a folder
- Creates a text file
- Stores student information
- Creates Backup directory
- Copies file
- Displays completion message

**Script**

```bat
@echo off

REM Set CMD window title
title OS Lab Student Automation

REM Ask for student name
set /p name=Enter student name: 

REM Create main folder
mkdir Student_Record

REM Enter folder
cd Student_Record

REM Create student information file
echo Student Name: %name% > student.txt
echo Course: Operating Systems >> student.txt
echo Lab: Batch Scripting >> student.txt

REM Create backup folder if it does not exist
if not exist Backup mkdir Backup

REM Copy information file into backup
copy student.txt Backup

REM Display contents
echo.
echo Student Record:
type student.txt

echo.
echo Automation completed successfully.

pause
```

### Line-by-Line Explanation

| Command | Explanation |
| --- | --- |
| `@echo off` | Keeps output clean |
| `title OS Lab Student Automation` | Sets the CMD window title |
| `set /p name=Enter student name:` | Accepts input |
| `mkdir Student_Record` | Creates the main directory |
| `cd Student_Record` | Moves inside the directory |
| `echo Student Name: %name% > student.txt` | Creates a file and stores the student's name |
| `echo Course: Operating Systems >> student.txt` | Adds another line without deleting previous content |
| `if not exist Backup mkdir Backup` | Creates Backup only if it does not already exist |
| `copy student.txt Backup` | Creates a backup copy |
| `type student.txt` | Displays the file contents |
| `pause` | Prevents the window from closing immediately |

---

## 16. Worked Examples

### 16.1 Basic Example

**Problem:** Create a Batch file that creates three folders: `Theory`, `Lab`, `Assignment`.

```bat
@echo off

mkdir Theory
mkdir Lab
mkdir Assignment

pause
```

### 16.2 Intermediate Example

**Problem:** Ask the user for their name and registration number, then save both in a file.

```bat
@echo off

set /p name=Enter Name: 
set /p reg=Enter Registration Number: 

echo Name: %name% > student.txt
echo Registration Number: %reg% >> student.txt

type student.txt

pause
```

### 16.3 Problem-Solving Example

**Scenario:** A department stores a daily report in `report.txt`. You need to automatically create a Backup folder and copy the report into it, **but only if the file exists**.

```bat
@echo off

if exist report.txt (

    if not exist Backup mkdir Backup

    copy report.txt Backup

    echo Report backup completed.

) else (

    echo ERROR: report.txt does not exist.

)

pause
```

**Why is this better than blindly copying?** The script checks the condition first. This prevents the script from assuming that the required input exists.

---

## 17. Practical Questions with Solutions

### Question 1 — Basic

Create a Batch script that prints `Welcome to Operating Systems Lab`.

```bat
@echo off
echo Welcome to Operating Systems Lab
pause
```

### Question 2 — Basic

Create three directories: `Windows`, `Linux`, `Backup`.

```bat
@echo off

mkdir Windows
mkdir Linux
mkdir Backup

pause
```

### Question 3 — Intermediate

Ask the user to enter a folder name and create that folder.

```bat
@echo off

set /p folder=Enter folder name: 

mkdir "%folder%"

echo Folder created successfully.

pause
```

**Why quotation marks?** If the user enters `Operating Systems`, the quotes help CMD treat it as one directory name.

### Question 4 — Intermediate

Determine whether `assignment.txt` exists.

```bat
@echo off

if exist assignment.txt (
    echo Assignment file found.
) else (
    echo Assignment file not found.
)

pause
```

### Question 5 — Problem Solving

Automatically create folders `Week1`, `Week2`, ... `Week10`.

```bat
@echo off

for /L %%i in (1,1,10) do (
    mkdir Week%%i
)

echo All folders created.

pause
```

---

## 18. Student Hands-On Activity

### Scenario — Automatic Lab Workspace Creator

You are responsible for preparing directories for a new course. Create a Batch script that:

- [ ] Asks for the course name.
- [ ] Creates a directory using that name.
- [ ] Creates the subfolders: `Lectures`, `Labs`, `Assignments`, `Backup`.
- [ ] Creates `course_info.txt`.
- [ ] Writes the course name into the file.
- [ ] Copies the file to `Backup`.
- [ ] Displays the directory structure.
- [ ] Displays a successful-completion message.

---

## 19. Instructor Solution

One possible solution:

```bat
@echo off

REM Ask user for course name
set /p course=Enter course name: 

REM Create main course directory
mkdir "%course%"

REM Move into main directory
cd "%course%"

REM Create subdirectories
mkdir Lectures
mkdir Labs
mkdir Assignments
mkdir Backup

REM Create course information
echo Course Name: %course% > course_info.txt

REM Copy information file to backup
copy course_info.txt Backup

REM Display directory structure
tree /f

REM Display completion message
echo.
echo Course workspace created successfully.

pause
```

---

## 20. Common Student Mistakes

### Mistake 1 — Saving as `.txt`

```text
Incorrect:  script.bat.txt
Correct:    script.bat
```

Use **Save as type → All Files**.

### Mistake 2 — Forgetting `%` around variables

```bat
:: Incorrect — prints the word "name"
echo name

:: Correct
echo %name%
```

### Mistake 3 — Using `%i` instead of `%%i` in a Batch file

In interactive CMD, a loop variable may use `%i`. Inside a Batch file, use `%%i`. This difference is important.

### Mistake 4 — Overwriting a file accidentally

```bat
:: Overwrites previous contents
echo New Line > notes.txt

:: Appends instead
echo New Line >> notes.txt
```

### Mistake 5 — Running the script repeatedly

A command such as `mkdir Backup` may show an error if the folder already exists. Better:

```bat
if not exist Backup mkdir Backup
```

---

## 21. Troubleshooting

| Problem | Solution |
| --- | --- |
| Batch file opens and immediately closes | Add `pause` at the end while testing |
| Variable appears blank | Check whether you used `%variable%` correctly |
| Folder names containing spaces cause errors | Use quotes: `mkdir "Operating Systems"` |
| Script cannot modify a protected directory | The location may require Administrator privileges. For lab practice, use a safe user directory such as `Documents`, `Desktop`, or a dedicated lab folder |

---

## 22. Important Safety Notes

Batch files can perform repetitive operations very quickly. Therefore, students should be particularly careful with commands such as:

```text
del
rmdir
move
```

**Never practice destructive scripts on:**

- `C:\Windows`
- `C:\Program Files`
- Important personal folders
- Network drives

> **Use a dedicated test directory.** For example: `C:\OSLabPractice`

---

## 23. Instructor Notes

A very effective teaching method is to start with this manual sequence:

```bat
mkdir Backup
copy notes.txt Backup
echo Backup Complete
```

Ask students: *"What happens if I need to execute these commands every day?"* Then put the same commands into `backup.bat` and execute it. This demonstrates automation immediately.

Another excellent live demonstration is:

```bat
for /L %%i in (1,1,20) do mkdir Student%%i
```

Before executing it, ask: *"How long would it take to manually create 20 folders?"* Then execute the script. Students immediately see why automation is useful.

---

## 24. Quick Knowledge Check

| # | Question | Answer |
| --- | --- | --- |
| Q1 | What is a Batch file? | A text file containing Windows commands that execute sequentially |
| Q2 | Which extension is commonly used? | `.bat` |
| Q3 | What does `@echo off` do? | Hides command lines from normal output |
| Q4 | What does `REM` mean? | Remark/comment |
| Q5 | Which command accepts user input? | `set /p` |
| Q6 | How is a variable accessed? | Using `%variable%` |
| Q7 | What does `>` do? | Redirects output and creates/overwrites a file |
| Q8 | What does `>>` do? | Appends output to a file |
| Q9 | Which statement is used for decisions? | `if` |
| Q10 | Which command creates loops? | `for` |

---

## 25. Viva Questions

| # | Question | Answer |
| --- | --- | --- |
| Q1 | What is Batch scripting? | The process of storing Windows command-line commands inside a script file for sequential or automated execution |
| Q2 | Why is automation useful? | It reduces repetitive manual work, saves time, and can make recurring operations more consistent |
| Q3 | What is the difference between CMD and a Batch file? | CMD allows commands to be entered interactively, while a Batch file stores commands for repeated/sequential execution |
| Q4 | What does `pause` do? | Waits for a key press |
| Q5 | What is `set /p` used for? | It accepts user input |
| Q6 | Explain `%name%`. | It retrieves the value stored in the variable `name` |
| Q7 | Difference between `>` and `>>`? | `>` overwrites/creates; `>>` appends |
| Q8 | Why do we use IF statements? | To make decisions based on conditions |
| Q9 | What does `IF EXIST` do? | Checks whether a file or directory exists |
| Q10 | Why are loops useful? | They allow repeated operations to be performed automatically |

---

## 26. Lab Task and Submission

### Task — Automatic Student Record Generator

Create a Batch script named **`student_record.bat`**.

The script must:

- [ ] Ask for student name.
- [ ] Ask for registration number.
- [ ] Ask for semester.
- [ ] Create a folder named after the registration number.
- [ ] Create `student.txt`.
- [ ] Save student details into the file.
- [ ] Create a `Backup` folder.
- [ ] Copy `student.txt` into `Backup`.
- [ ] Check whether the backup file exists.
- [ ] Display `Backup Successful` if it exists.
- [ ] Display the complete directory structure.
- [ ] Pause before exiting.

### Submission Requirements

Students should submit:

- `.bat` file
- Screenshot of execution
- Screenshot of final directory structure
- Short explanation of each command
- Output file created by the script

---

## 27. Lecture Summary

In this lab, students progressed from **manual command execution to Windows automation**. The learning sequence was:

```text
Individual CMD Commands
        ↓
Batch File
        ↓
Variables
        ↓
User Input
        ↓
Conditions
        ↓
Loops
        ↓
Automation
```

**Syntax and commands covered:**
`@echo off` · `echo` · `pause` · `REM` · `set` · `set /p` · `set /a` · `if` · `if exist` · `if not exist` · `for` · `for /L` · `>` · `>>`

> **Key concept:** A Batch script combines operating-system commands with basic programming logic so that Windows tasks can be performed automatically.

---

## 28. Batch Scripting Cheat Sheet

| Syntax / Command | Purpose | Example |
| --- | --- | --- |
| `@echo off` | Hide command display | `@echo off` |
| `echo` | Display text | `echo Hello` |
| `echo.` | Blank line | `echo.` |
| `pause` | Wait for key press | `pause` |
| `REM` | Add comment | `REM Create backup` |
| `set` | Create variable | `set name=Ali` |
| `set /p` | Take user input | `set /p name=Enter Name:` |
| `%var%` | Read variable value | `%name%` |
| `set /a` | Arithmetic | `set /a sum=10+20` |
| `>` | Create/overwrite file | `echo Hello > a.txt` |
| `>>` | Append to file | `echo More >> a.txt` |
| `if` | Decision making | `if %age% GEQ 18 ...` |
| `if exist` | Check existence | `if exist a.txt ...` |
| `if not exist` | Check absence | `if not exist Backup mkdir Backup` |
| `for` | Repeat operations | `for %%i in (...) do ...` |
| `for /L` | Numeric loop | `for /L %%i in (1,1,5) ...` |
| `title` | CMD window title | `title OS Lab` |

---

## 29. Connection to Lab 4

Students have now learned the progression:

```text
Windows GUI
     ↓
CMD Commands
     ↓
Batch Automation
```

These skills form the foundation for the next lab.

---

<p align="center"><b>Operating Systems Lab · Lab 03</b><br>Batch Scripting &amp; Windows Automation</p>
