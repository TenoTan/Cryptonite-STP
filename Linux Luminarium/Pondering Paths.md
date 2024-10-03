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
## Position Thy Self
This challenge involved going to a specific directory to acess the flag using `/challenge/run`. 
On running the terminal, I tried going into the directory directly, and got the following result:
```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /proc/68 directory.
Please use the `cd` utility to change directory appropriately.
```
After reading the msg carefully, I noticed it mentioned not being in the `/proc/68` directory. I then went to the given directory.
```
hacker@paths~position-thy-self:~$ cd /proc/68
hacker@paths~position-thy-self:/proc/68$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QL_pyrPdIpnL_5JTD4pnsu34C7B.dZDN1QDLyUDN1czW}

```
Flag found!

## Position Elsewhere
This challenged followed same process as of the above challenge.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/build-essential
hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EQnT3UEbS5bFCGY69h9NXovWH3a.ddDN1QDLyUDN1czW}
```

## Position yet elsewhere

Same process as the above challenge.

```
acker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc
hacker@paths~position-yet-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Esr_d0Q19qWtFMlJlAmXKTchwEL.dhDN1QDLyUDN1czW}
```

## implicit relative paths, from /

### About Relative Paths:
* If my cwd is `/`, then a relative path to the file is `tmp/a/b/my_file`.
* If my cwd is `/tmp`, then a relative path to the file is `a/b/my_file`.
* If my cwd is `/tmp/a/b/c`, then a relative path to the file is `../my_file`. The `..` refers to the parent directory.

In the challenge, it is implied that we got to the `/` directory to run the command. Once we are already in the root (`/`) directory, we don't need to run `/challenge/run` again, because we are already in the root directory.

```
cd /challenge/run
cd /
challenge/run
```
The output gave us the flag.

## Explicit Relative Paths, from /

Relative path: `.`

```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{c3oBuD4SY_p1ANFQqoiUWK1aeHA.dBTN1QDLyUDN1czW}
```

## Implicit Relative Path
Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path.

I made multiple mistakes in trying to figure out the right way to call the relative path, but in the end, `./run` worked.
```
hacker@paths~implicit-relative-path:/challenge$ run
ssh-entrypoint: run: command not found
hacker@paths~implicit-relative-path:/challenge$ /run
ssh-entrypoint: /run: Is a directory
hacker@paths~implicit-relative-path:/challenge$ .run
ssh-entrypoint: .run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Ql1V4vsCcIhMD5ZY6Ieb7mSclui.dFTN1QDLyUDN1cz
```

