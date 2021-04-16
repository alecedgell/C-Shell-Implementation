Use the command "make" to compile the code. The code is then compiled and created a runnable "shell". 
Enter "./shell" into the terminal to execute the program. "make clean" will remove the compiled files.
We could not figure out how to get pipes to work correctly. The program will halt if a process is put
in the background as the first command. Background processes seem to work the rest of the time. The special
symbols also seem to be working correctly. The "->" prompt will print in the wrong place if a process prints
to the terminal from the background, but commands can still be ran.