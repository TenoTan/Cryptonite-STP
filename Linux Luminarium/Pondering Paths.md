# Linux File Paths
Linux filesystem is a tree.

## Challenge: The Root
This challenge is about exploring and understanding the file system. 
I simply searched for the pwn directory and found the flag.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{EflXBbcFdRux-OOi_tvIojAlmMI.dhzN5QDLyUDN1czW}
```
## Program and Absolute Path
This challenge involves using absolute paths. The flag lies in the `run` directory in the `challenge` directory inside the root `/`.
The absolute paths, thus, is `/challenge/run`.
Executing this gives us the flag.
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{sKdW3QIU2dXgbtV9Azj_CLs8lA_.dVDN1QDLyUDN1czW}
```
