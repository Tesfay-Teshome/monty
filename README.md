# Monty Interpreter in C

Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project was to create an interpreter for Monty ByteCodes files in C language.


# Synopsis

**Monty byte code files**

Files containing Monty byte codes usually have the  `.m`  extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument and the file can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:

    Example:
    File monty_test.m

```
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$

push 2
  push 3
                   pall    


                           
push 4

    push 5    
      push    6        

pall This is the end of our program. Monty is awesome!$
```

**Program Usage:**

The Interpreter must be given a valid Monty byte code file and run in the way:

Usage: `monty file`

As mentioned before, the file extension is optional.

```
Example:

test@ubuntu:~/monty$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
test@ubuntu:~/monty$ ./monty bytecodes/00.m
3
2
1
test@ubuntu:~/monty$
```

The bytecodes that can be interpreted by the program are the following:


|Bytecode| Function |
|--|--|
| push | Pushes an element to the stack (Requires an integer argument)|
| pall | Prints all the values on the stack, starting from the top of the stack |
| pint | Prints the value at the top of the stack, followed by a new line |
| pop | Removes the top element of the stack |
| swap | Swaps the top two elements of the stack |
| add | Adds the top two elements of the stack |
| nop | Doesn’t do anything |
| sub | Subtracts the top element of the stack from the second top element of the stack |
| div | Divides the second top element of the stack by the top element of the stack. |
| mul | Multiplies the second top element of the stack with the top element of the stack |
| mod | Computes the rest of the division of the second top element of the stack by the top element of the stack |
| pchar | Prints the char at the top of the stack, followed by a new line |
| pstr | Prints the string starting at the top of the stack, followed by a new line |
| rotl | Rotates the stack to the top |
| rotr | Rotates the stack to the bottom |
| stack | Sets the format of the data to a stack (LIFO). This is the default behavior of the program |
| queue | sets the format of the data to a queue (FIFO) |


**Comments:**

Besides the bytecodes interpreted, the program allows for commentary in the monty files.

For this when the first non-space character of a line is `#`, the line won't be taken into account in execution.


```
Example:

test@ubuntu:~/monty$ cat -e bytecodes/00.m
push 1$
push 2$
#Comment$
push 3$
pall$
test@ubuntu:~/monty$ ./monty bytecodes/00.m
3
2
1
test@ubuntu:~/monty$
```


## General Use Examples

```
test@ubuntu:~/monty$ cat bytecodes/01.m 
push 1
push 2
push 3
pall
add
pall

est@ubuntu:~/monty$ ./monty bytecodes/01.m 
3
2
1
5
1
test@ubuntu:~/monty$
```


```
test@ubuntu:~/monty$ cat bytecodes/02.m 
push 72
pchar
test@ubuntu:~/monty$ ./monty bytecodes/02.m 
H
test@ubuntu:~/monty$
```


```
test@ubuntu:~/monty$ cat bytecodes/03.m 
push 1
push 2
push 3
push 4
push 5
push 6
push 7
push 8
push 9
push 0
pall
rotl
pall
test@ubuntu:~/monty$ ./monty bytecodes/03.m 
0
9
8
7
6
5
4
3
2
1
9
8
7
6
5
4
3
2
1
0
test@ubuntu:~/monty$ 
```


## Built with

Ubuntu 20.04, Emacs, Vim, and C language.

## Authors

Tesfay Teshome and Helina Gebreyes


## bf Folder

There is some extra files found in the bf folder. These files correspond to different codes written in Brainf*ck programming language.

|File| Function |
|--|--|
| 1000-school.bf | Prints the word "school" followed by a new line|
| 1001-add.bf | Adds two 1 digit numbers provided by an user (the result must be < 10) |
|1002-mul.bf | Multiplies two 1 digit numbers provided by an user (the result must be < 10) |
| 1003-mul.bf | Multiplies two 1 digit numbers provided by an user |


In order to run these files, a Brainf*ck interpreter must be used.
