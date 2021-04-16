# C-Shell-Implementation
Creation of a C shell to execute a specific list of commands given by the professor.
We could not figure out how to get pipes to work correctly. The program will halt if a process is put in the background as the first command. 
Background processes seem to work the rest of the time. 
The special symbols also seem to be working correctly. 
The "->" prompt will print in the wrong place if a process prints to the terminal from the background, but commands can still be ran.

---

## Instructions
#### To compile, use: (Note: This will generate an executeable "shell" file.)
```bash
make
```



#### To execute, use:
```bash
./shell
```

#### To remove compliled files, use:
```bash
make clean
```

### Requirements
1. The internal shell command "exit" which terminates the shell.
    - Concepts: shell commands, exiting the shell
    - System calls: exit()

2. A command with no arguments
    - Example: **ls**
    - Details: Your shell must block until the command completes and, if the return code is
      abnormal, print out a message to that effect.
    - Concepts: Forking a child process, waiting for it to complete, synchronous execution
    - System calls: **fork(), execvp(), exit(), wait()**

3. A command with arguments
    - Example: **ls -l**
    - Details: Argument 0 is the name of the command
    - Concepts: Command-line parameters


4. A command, with or without arguments, whose output is redirected to a file
    - Example: **ls -l > foo**
    - Details: This takes the output of the command and put it in the named file
    - Concepts: File operations, output redirection. 
    - System calls: **freopen()**



5. A command, with or without arguments, whose output is appended to a file
    - Example: **ls -l >> foo**
    - Details: This is an append, which is a variation of the output redirect (see above)

6. A command, with or without arguments, whose input is redirected from a file
    - Example: **sort < testfile**
    - Details: This takes the named file as input to the command
    - Concepts: Input redirection, more file operations
    - System calls: **freopen()**

7. A command, with or without arguments, executed in the background using &.
   *For simplicity, assume that if present the & is always the last thing on the line.*
    - Example: **vi &**
    - Details: In this case, your shell must execute the command and return immediately, not 
      blocking until the command finishes. The distinction must be made between
      backgrounding a process that does not need interactive input and one that does, e.g., the
      ***who*** command vs. the ***vi*** command.
    - Concepts: Background execution, signals, signal handlers, process groups, asynchronous
      execution.
    - System calls: **sigset(), sigaction()** 
    - Signals: **SIGTTOU**

8. A command, with or without arguments, whose output is piped to the input of another command.
    - Example: ls -l | more
    - Details: This takes the output of the first command and makes it the input to the second command.
    - Concepts: Pipes, synchronous operation System calls:** pipe() **
      _Note: You must check and correctly handle all return values. This means that you need to read 
    the man pages for each function to figure out what the possible return values are, what errors 
    they indicate, and what you must do when you get that error. _
