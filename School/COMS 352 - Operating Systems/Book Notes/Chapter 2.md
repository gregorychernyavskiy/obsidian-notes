*Everything is from Chapter 2 of the book.*

**So what happens when a program runs?**
Well, a running program does one very simple thing: it executes instructions. Many millions (and these days, even billions) of times every second, the processor *fetches* an instruction from memory, *decodes* it (i.e., figures out which instruction this is), and *executes* it (i.e., it does the thing that it is supposed to do, like add two numbers together, access memory, check a condition, jump to a function, and so forth). After it is done with this instruction, the processor moves on to the next instruction, and so on, and so on, until the program finally completes.

**Operating System** is in charge of making sure the system operates correctly and efficiently in an easy-to-use manner.

The primary way the OS does this is through a general technique that we call **virtualization**. The OS takes a physical resource (such as the processor, or memory, or disk) and transforms it into a more general, powerful, and easy-to-use **virtual** form of itself. So we refer to the Operating System as the **Virtual Machine**.

A typical OS exports a few hundred system calls that are available to applications. The OS provides those calls to run programs, access memory and devices, and other related actions, we also sometimes say that the OS provides a **standard library** to applications.

Finally, because virtualization allows many programs to run (thus sharing the CPU), and many programs to concurrently access their own instructions and data (thus sharing memory), and many programs to access devices (thus sharing disks and so forth), the OS is sometimes known as a resource manager. Each of the CPU, memory, and disk is a resource of the system; it is thus the operating system’s role to manage those resources, doing so efficiently or fairly or indeed with many other possible goals in mind. To understand the role of the OS a little bit better, let’s take a look at some examples.



***2.1 VIRTUALIZING THE CPU***
**Simple code that loops and prints**
```c
#include <stdio.h>
#include <stdlib.h>
#include <sys/time.h>
#include <assert.h>
#include "common.h"

int main(int argc, char *argv[])
{
    if (argc != 2) {
        fprintf(stderr, "usage: cpu <string>\n");
        exit(1);
    }
    char *str = argv[1];
    while (1) {
        Spin(1);
        printf("%s\n", str);
    }
    return 0;
}
```

**Spin()** is a function that repeatedly checks the time and returns once it has run for a second. Then, it prints out the string that the user passed in on command line, and repeats it forever. 

**Virtualizing the CPU:**
- is turning a single CPU into a seemingly infinite number of CPUs and thus allowing many programs to seemingly run at once.

***VIRTUALIZING THE MEMORY***
**A Program That Accesses Memory**
```c
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include "common.h"

int main(int argc, char *argv[])
{
    int *p = malloc(sizeof(int)); // a1
    assert(p != NULL);
    printf("(%d) address pointed to by p: %p\n",
           getpid(), p); // a2
    *p = 0; // a3
    while (1) {
        Spin(1);
        *p = *p + 1;
        printf("(%d) p: %d\n", getpid(), *p); // a4
    }
    return 0;
}
```


The model of **physical memory** presented by modern machines is very simple. **Memory** is just an array of bytes; to read memory, one must specify an address to be able to access the data stored there; to write (or update) memory, one must also specify the data to be written to the given address.

Memory is accessed all the time when the program is running. A program keeps all of its data structured in memory, and accesses them through that access memory in doing their work. Each instruction of the program is in memory too; thus memory is accessed on each instruction fetch.

**Running the memory program multiple times:**
- First the program allocates some memory.
- Then it prints out the address of the memory.
- And then it puts the number zero into the first slot of the newly allocated memory.
- Finally, the program loops, delaying for a second and incrementing the value stored at the address held in p.
- With every print statement it also prints out what is called the process identifier (the PID) of the running program.
- The PID is unique per running process.

Each program has it's own private memory, instead of sharing the same physical memory with other running programs.

This is exactly what happens here as the OS is virtualizing memory. Each process accesses its own private virtual address space, which the OS somehow maps onto the physical memory of the machine. A memory reference within one running program does not affect the address space of other processes (or the OS itself); as far as running program is concerned, it has physical memory all to itself. The reality is that that physical memory is a shared source, managed by operating system. Exactly, how all of this is accomplished is also the subject of the first part of this book, on the topic of **VIRTUALIZATION**.

