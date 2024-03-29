# Pipex

## Introduction

In this projec't we'll make our own implementation of the pipes we know and love from shell (``|``). To do so, we will start using a whole new set of functions that will introduce to us the concept of multiple processes, using pipes, forks and dups.

## How it works (Shell)

In this project we are asked to code a program which will immitate the behavior of this shell command:

```shell
❯ < file1 cmd1 | cmd2 > file2
```
The idea of the program is that we take an infile and two commands, and pass the infile as the standard input to the first command, and then pipe the output of the first command to the second command, and finally save it all to a second file. Now that we've seen the command, let's break it down:

* ``<``: Used to denote that we will be passing the next argument as the standard input (stdin)
* ``file1``: Path to the file we want to open as the standard input. It must exist and should be opened read-only
* ``cmd1``: First command. It will receive the stdin and run a command with it, if applicable
* ``|``: Transforms the standard output (stdout) of the first command into the standard input (stdin) for the next command
* ``cmd2``: Receives the standard output of the first command as stdin and runs a command with it, if applicable
* ``>``: Redirects whatever is on the standard output (stdout) into a file, creating it if it does not exist
* ``file2``: Path to an output file which may or may not exist. If it exists, it will be truncated (emptied) and should be opened write-only

## How to Run

Our own implementation of the previous command will have a similar look. We will compile an executable called ``pipex``, which will only accept 4 commands in the mandatory part. This is what it expects to receive:

```shell
❯ ./pipex file1 cmd1 cmd2 file2
```

You need to create file1 and file2 (at least file1)

Examples
```c
❯ ./pipex file1 "ls -l" "wc -l" file2
```

Should behave like: ```shell < file1 ls -l | wc -l > file2 ```

```c
❯ ./pipex file1 "grep a1" "wc -w" file2
```

Should behave like: ```shell < file1 grep a1 | wc -w > file2```
