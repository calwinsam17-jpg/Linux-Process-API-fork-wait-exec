# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:


## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int pid = fork();

    if (pid == 0) { 
        printf("I am child, my PID is %d\n", getpid()); 
        printf("My parent PID is: %d\n", getppid()); 
        sleep(2);  // Keep child alive for verification
    } else { 
        printf("I am parent, my PID is %d\n", getpid()); 
        wait(NULL); 
    }
}
```

##OUTPUT

<img width="740" height="190" alt="Screenshot 2026-02-16 085610" src="https://github.com/user-attachments/assets/703a9b5e-4476-4395-a9d8-03549112e2eb" />







## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family

```
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    pid_t pid = fork();

    if (pid == 0)
    {
        printf("Child process executing ls command\n");
        execlp("ls", "ls", NULL);
        perror("Exec failed");
        exit(1);
    }
    else
    {
        wait(NULL);
        printf("Parent process: Child execution completed\n");
    }

    return 0;
}
```
























##OUTPUT

<img width="716" height="250" alt="Screenshot 2026-02-16 085812" src="https://github.com/user-attachments/assets/46de5bcd-47dd-4d02-8622-a486f0ba7682" />

















# RESULT:
The programs are executed successfully.
