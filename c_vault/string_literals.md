---
id: "string_literals"
aliases:
  - "string_literals"
  - "String literals and .rodata:"
tags: []
---
`
char *str;
str = "string";

char s[] = "string";
` 
In the case of a string literal it is stored automatically but only readable. 
Attempting to change any characters in this string will result in a segfault.

The code 'char s[] = "string"' holds a copy of the string so specific characters 
can be accessed/changed.

# String literals and .rodata:
String literals are stored in your executable at compilation. The way it is stored depends 
on the operating system and linker.

## Compile procsess (for most systems):
* Compiler places the string into read-only data section (__.rodata__).
* Linker collects all the data in the read-only sections and places them in  a special segement.
It is then places in the executable.

One way to check that a string literal is stored in the executable file is to use the __'strings'__ command.
($ man strings)
Example:
`gcc segf.c -o segf
-> string segf`

It is also possible to use objdump to print the .rodata contents.
Example:
`objdump -s -j .rodata segf`
