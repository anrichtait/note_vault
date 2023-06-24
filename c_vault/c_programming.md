This is the main note file for the C programming notebook. 
With my current understanding of obsidian it will work sort of like a quick 
review or reference with links to other notes that go more in depth on a concept.
# [[alx_projects]]
# [[useful_functions]]

# [[pointers]] and arrays:
A typical machine has an array of consecutively addressed memory cells that can be
 manipulated individually or in contigous(next to or together in sequence) groups. 
So a pointer is basically a group of cells that can hold an address.

## Syntax:
`type *variable;`

So the declaration:
`float *p;`
identifies p as a pointer variable of type "pointer to float". This means that any 
data with the float data type can be stored via memory in variable p.

# Automatic and dynamic allocation, [[malloc()]] and [[free()]]

## Automatic allocation:
Automatic allocation occurs whenever a variable or string literal is declared/used.
In these cases memory is not controlled by the programmer.

```c
int main(void)
{
int i;
char c;  
int *ptr;  
char string[3];  
}
```

The program handles memory allocation when the function is called. In this case 
the main() function.
When the function is exited all designated memory is freed.

There is one special case in the context of automatic allocation: [[string_literals]]

__So then if automatic allocation is available why use dynamic allocation?__

-> Dynamic allocation is used in cases where the programmer does not know how much 
memory will need to be allocated.

## Dynamic Allocation:
Dynamic allocation is handled by a few main functions, those being:
* [[malloc()]]: allocates a specific number of bytes in memory and returns a pointer 
to the allocated memory. The memory will have read and write permissions.
* [[free()]]: frees memory that was allocated by 'malloc(), calloc() or realloc()'.
* [[calloc()]]: This function is similar to malloc but also initializes the 
allocated memory to zero. It takes two arguments: the number of elements to allocate 
and the size of each element. The total amount of memory allocated is calculated as 
the product of the two arguments.
* [[realloc()]]: his function is used to resize a previously allocated memory block. 
It takes two arguments: a pointer to the previously allocated memory block and the 
new size in bytes. It returns a pointer to the resized memory block. If the 
reallocation fails, it returns a null pointer. Note that realloc can also be used 
to allocate memory if the provided pointer is null.

Taking memory management into your own hands has some serious dangers and pitfalls, 
to assist with making memory management easier we can use tools like [[gdb]] and [[valgrind]].

## Should you [[cast]] the result of [[malloc()]]?
__Generally NO__

## [[string_literals]] and .rodata:
String literals are stored in your executable at compilation. The way it is stored depends 
on the operating system and linker.
