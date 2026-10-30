💻 Operating Systems Lab

<p align="center">
<img src="https://img.shields.io/badge/Language-C-blue?style=for-the-badge&logo=c" />
<img src="https://img.shields.io/badge/Subject-Operating%20Systems-purple?style=for-the-badge" />
<img src="https://img.shields.io/badge/Platform-Linux-orange?style=for-the-badge&logo=linux" />
</p>

<p align="center">
<b>📚 A collection of Operating Systems Lab programs implemented in C.</b>
<br>
Exploring processes, system calls, process management, and core OS concepts.
</p>

📌 Table of Contents
Introduction
Practical 01 – Get Process ID
Practical 02 – Process Creation Using fork
How to Compile and Run
Key Concepts
Learning Outcomes
🌟 Introduction

Welcome to my Operating Systems Lab Repository!

This repository contains practical implementations of important Operating System concepts using the C programming language on Linux.

The objective is to understand how an operating system manages processes, handles system calls, and coordinates the execution of programs.

Each practical includes:

📝 Problem statement
💻 C source code
▶️ Sample output
📖 Explanation of important concepts
🖥️ Practical 01 – Get Process ID
🎯 Aim

To write a C program to display the Process ID (PID) of the currently executing process using the getpid() system call.

💡 Theory

A Process ID (PID) is a unique numerical identifier assigned by the operating system to every running process.

The getpid() system call returns the PID of the calling process.

💻 Source Code
c
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("Current PID:%d\n", getpid());
    return 0;
}

📤 Sample Output
text
Current PID: 2456


Note: The PID may differ each time the program executes.

🔍 Code Explanation
Function	Description
stdio.h	Provides standard input/output functions.
unistd.h	Provides access to POSIX system calls.
getpid()	Returns the current process ID.
printf()	Displays the process ID.
return 0	Indicates successful program termination.
📚 Key Concept

PID (Process ID): A unique identifier used by the operating system to identify and manage a process.

👨‍👦 Practical 02 – Process Creation Using fork()
🎯 Aim

To write a C program to create a child process using the fork() system call and make the parent process wait for the child to terminate using wait().

💡 Theory

The fork() system call creates a new process called the child process by duplicating the calling process, known as the parent process.

After calling fork(), two processes execute:

👨 Parent Process – The original process.
👶 Child Process – The newly created process.

The wait() system call makes the parent process wait until a child process terminates.

💻 Source Code
c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t p = fork();

    if(p == 0) {
        printf("Child Running with PID:%d\n", getpid());
        sleep(0);
        printf("Child Exiting...\n");
        exit(0);
    }
    else {
        printf("Parent Waiting for child to terminate...\n");
        pid_t terminated_pid = wait(NULL);
        printf("Parent Terminated Child PID:%d\n", terminated_pid);
    }

    return 0;
}

📤 Sample Output
text
Parent Waiting for child to terminate...
Child Running with PID: 2460
Child Exiting...
Parent Terminated Child PID: 2460


Note: The execution order of the first parent and child messages may vary because process scheduling is controlled by the operating system.

🔍 Code Explanation
Function	Description
fork()	Creates a new child process.
pid_t	Data type used to store process IDs.
p == 0	Checks whether the executing process is the child.
getpid()	Returns the current process ID.
sleep(0)	Requests a zero-second sleep; it does not provide a meaningful delay.
exit(0)	Terminates the child process successfully.
wait(NULL)	Waits for a child process to terminate.
printf()	Displays messages on the terminal.
🧠 Understanding fork()

The return value of fork() determines which process is executing:

Return Value	Meaning
0	Executed by the child process.
Positive value	Executed by the parent; value is the child's PID.
-1	Process creation failed.
🔄 Process Execution Flow
text
             START
               |
               v
          Call fork()
               |
        +------+------+
        |             |
        v             v
   Child Process  Parent Process
        |             |
        v             v
   Print Child    Print Waiting
       PID          Message
        |             |
        v             v
   Child Exits     Call wait()
        |             |
        +------+------+
               |
               v
       Child Terminated
               |
               v
       Parent Continues
               |
               v
              END

⚙️ How to Compile and Run

Make sure GCC is installed on your Linux system.

Step 1: Install GCC
bash
sudo apt update
sudo apt install gcc

Step 2: Compile Practical 01
bash
gcc pid.c -o pid

Step 3: Execute Practical 01
bash
./pid

Step 4: Compile Practical 02
bash
gcc fork.c -o fork

Step 5: Execute Practical 02
bash
./fork

📖 Key Concepts Covered
Concept	Description
Process	A program currently under execution.
PID	Unique identification number of a process.
getpid()	Retrieves the current process ID.
fork()	Creates a child process.
wait()	Synchronizes the parent with child termination.
Parent Process	The process that creates another process.
Child Process	The process created using fork().
Process Synchronization	Coordination between processes.
🎓 Learning Outcomes

After completing these practicals, I learned:

How to retrieve the Process ID using getpid().
How a new process is created using fork().
The difference between parent and child processes.
How to identify processes using the return value of fork().
How to synchronize process execution using wait().
How Linux handles basic process management.
🚀 Future Practicals

More Operating Systems experiments will be added to this repository, covering:

Process Creation and Management
CPU Scheduling Algorithms
Inter-Process Communication (IPC)
Threads and Multithreading
Process Synchronization
Semaphores and Mutex Locks
Deadlock Handling
Memory Management
Page Replacement Algorithms
Disk Scheduling Algorithms

<p align="center">
⭐ <b>Learning Operating Systems, One Practical at a Time!</b> ⭐
<br><br>
Made with ❤️ using C Programming
</p>
