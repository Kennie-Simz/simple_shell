# Project Name
**0x16. C - Simple Shell**

## Table of Contents
- [Project Description](#project-description)
- [Requirements](#requirements)
- [Authorized functions and macros](#authorized-functions-and-macros)
- [Compilation](#compilation)
- [Tasks](#tasks)
- [Known Bugs](#known-bugs)
- [Collaborate](#collaborate)

### Project Description
Simple_shell is a command line interpreter, or shell, in the tradition of the first Unix shell written by Ken Thompson in 1971. This shell is intentionally minimalistic, yet includes the basic functionality of a traditional Unix-like command line user interface.

##  Requirements
*   Allowed editors: `vi`, `vim`, `emacs`.
*   All your files will be compiled on Ubuntu 20.04 LTS using gcc, using the options `-Wall -Werror -Wextra -pedantic -std=gnu89`.
*   Your code should use the `Betty` style. It will be checked using `betty-style.pl` and `betty-doc.pl`.
*   All your files should end with a new line.
*   You are not allowed to use global variables.
*   No more than 5 functions per file.
*   All your header files should be include guarded.
*   You should have an `AUTHORS` file at the root of your repository, listing all individuals having contributed content to the repository. Format, see [Docker](https://github.com/moby/moby/blob/master/AUTHORS).

##  Authorized functions and system calls
*   `access` (man 2 access)
*   `chdir` (man 2 chdir)
*   `close` (man 2 close)
*   `closedir` (man 3 closedir)
*   `execve` (man 2 execve)
*   `exit` (man 3 exit)
*   `_exit` (man 2 _exit)
*   `fflush` (man 3 fflush)
*   `fork` (man 2 fork)
*   `free` (man 3 free)
*   `getcwd` (man 3 getcwd)
*   `getline` (man 3 getline)
*   `getpid` (man 2 getpid)
*   `isatty` (man 3 isatty)
*   `kill` (man 2 kill)
*   `malloc` (man 3 malloc)
*   `open` (man 2 open)
*   `opendir` (man 3 opendir)
*   `perror` (man 3 perror)
*   `read` (man 2 read)
*   `readdir` (man 3 readdir)
*   `signal` (man 2 signal)
*   `stat` (__xstat) (man 2 stat)
*   `lstat` (__lxstat) (man 2 lstat)
*   `fstat` (__fxstat) (man 2 fstat)
*   `strtok` (man 3 strtok)
*   `wait` (man 2 wait)
*   `waitpid` (man 2 waitpid)
*   `wait3` (man 2 wait3)
*   `wait4` (man 2 wait4)
*   `write` (man 2 write)

## More Info
### Output

*   Unless specified otherwise, your program **must have the exact same output** as `sh` (`/bin/sh`) as well as the exact same error output.
*   The only difference is when you print an error, the name of the program must be equivalent to your `argv[0]` (See below).

Example of error with `sh`:

```
$ echo "qwerty" | /bin/sh
/bin/sh: 1: qwerty: not found
$ echo "qwerty" | /bin/../bin/sh
/bin/../bin/sh: 1: qwerty: not found
$
```

Same error with your program `hsh`:

```
$ echo "qwerty" | ./hsh
./hsh: 1: qwerty: not found
$ echo "qwerty" | ./././hsh
./././hsh: 1: qwerty: not found
$
```

### Compilation
Your code will be compiled this way:

```
$ gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh
```

### Testing
Your shell should work like this in interactive mode:

```
$ ./hsh
($) /bin/ls
hsh main.c shell.c
($)
($) exit
$
```

But also in non-interactive mode:

```
$ echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
$
$ cat test_ls_2
/bin/ls
/bin/ls
$
$ cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
$
```

We strongly encourage the entire class to work together to create a suite of checks covering both regular tests and edge cases for each task. 

# Tasks

**0. Betty would be proud**
---
Write a beautiful code that passes the Betty checks.

- - -

**1. Simple shell 0.1**
---
Write a UNIX command line interpreter.

*   Usage: `simple_shell`

Your Shell should:

*   Display a prompt and wait for the user to type a command. A command line always ends with a new line.
*   The prompt is displayed again each time a command has been executed.
*   The command lines are simple, no semicolons, no pipes, no redirections or any other advanced features.
*   The command lines are made only of one word. No arguments will be passed to programs.
*   If an executable cannot be found, print an error message and display the prompt again.
*   Handle errors.
*   You have to handle the “end of file” condition (`Ctrl+D`)

You don’t have to:

*   Use the `PATH`.
*   Implement built-ins.
*   Handle special characters : ", ', `, \\, *, &, #.
*   Be able to move the cursor
*   Handle commands with arguments

```
julien@ubuntu:~/shell$ ./shell 
#cisfun$ ls
./shell: No such file or directory
#cisfun$ /bin/ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell.c  stat.c         wait
env-environ.c  exec    fork    mypid   ppid   printenv  promptc  shell     stat test_scripting.sh  wait.c
#cisfun$ /bin/ls -l
./shell: No such file or directory
#cisfun$ ^[[D^[[D^[[D
./shell: No such file or directory
#cisfun$ ^[[C^[[C^[[C^[[C
./shell: No such file or directory
#cisfun$ exit
./shell: No such file or directory
#cisfun$ ^C
julien@ubuntu:~/shell$ echo "/bin/ls" | ./shell
#cisfun$ barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell.c stat.c         wait
env-environ.c  exec    fork    mypid   ppid   printenv  promptc  shell     stat test_scripting.sh  wait.c
#cisfun$ julien@ubuntu:~/shell$
```

- - -

**2. Simple shell 0.2**
---
Simple shell 0.1 +

*   Handle command lines with arguments.
- - -

**3. Simple shell 0.3**
---
Simple shell 0.2 +

*   Handle the `PATH`.
*   `fork` must not be called if the command doesn’t exist.

```
julien@ubuntu:~/shell$ ./shell_0.3
:) /bin/ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell_0.3  stat    test_scripting.sh  wait.c
env-environ.c  exec    fork    mypid   ppid   printenv  promptc  shell     shell.c    stat.c  wait
:) ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell_0.3  stat    test_scripting.sh  wait.c
env-environ.c  exec    fork    mypid   ppid   printenv  promptc  shell     shell.c    stat.c  wait
:) ls -l /tmp 
total 20
-rw------- 1 julien julien    0 Dec  5 12:09 config-err-aAMZrR
drwx------ 3 root   root   4096 Dec  5 12:09 systemd-private-062a0eca7f2a44349733e78cb4abdff4-colord.service-V7DUzr
drwx------ 3 root   root   4096 Dec  5 12:09 systemd-private-062a0eca7f2a44349733e78cb4abdff4-rtkit-daemon.service-ANGvoV
drwx------ 3 root   root   4096 Dec  5 12:07 systemd-private-062a0eca7f2a44349733e78cb4abdff4-systemd-timesyncd.service-CdXUtH
-rw-rw-r-- 1 julien julien    0 Dec  5 12:09 unity_support_test.0
:) ^C
julien@ubuntu:~/shell$ 
```

- - -

**4. Simple shell 0.4**
---
Simple shell 0.3 +

*   Implement the `exit` built-in, that exits the shell.
*   Usage: `exit`.
*   You don’t have to handle any argument to the built-in `exit`.

- - -

**5. Simple shell 1.0**
---
Simple shell 0.4 +

*   Implement the `env` **built-in**, that prints the current environment.

```
julien@ubuntu:~/shell$ ./simple_shell
$ env
USER=julien
LANGUAGE=en_US
SESSION=ubuntu
COMPIZ_CONFIG_PROFILE=ubuntu
SHLVL=1
HOME=/home/julien
C_IS=Fun_:)
DESKTOP_SESSION=ubuntu
LOGNAME=julien
TERM=xterm-256color
PATH=/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
DISPLAY=:0
$ exit
julien@ubuntu:~/shell$ 
```

**6. Simple shell 0.1.1**
---
Simple shell 0.1 +

*   Write your own `getline` function.
*   Use a buffer to read many chars at once and call the least possible the `read` system call.
*   You will need to use `static` variables.
*   You are not allowed to use `getline`.

You don’t have to:

*   Be able to move the cursor.

## Known Bugs
Not yet found.

### Collaborate

To collaborate, reach us through the email addresses in the AUTHORS file.