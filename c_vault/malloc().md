---
id: "malloc()"
aliases:
  - "Prototype:"
tags: []
---
This function is used to dynamically allocate memory at runtime. It takes the 
number of bytes to allocate as an argument and returns a pointer to the 
allocated memory block. If the allocation fails, it returns a null pointer.

# Prototype:
`void *malloc(size_t size);`
`void *`: pointer to the type of your choice.
`size`: is the number of bytes the program must allocate.
```c
int main(void)
{
    char *str;

    str = malloc(sizeof(char) * 3);
    str[0] = '0';
    str[1] = 'K';
    str[2] = '\0';
    printf("%s\n", str);
    return (0);
}
```
## Breakdown:
This will allocate 3 bytes of memory for the str variable. (1byte * 3 = 3bytes)
Keep in mind that using sizeof() is better than explicitly telling malloc() to 
allocate 3 bytes of space as it accounts for varying platforms where the byte sizes
of types aren't always the same.

# Should you [[cast]] the result of [[malloc()]]?
__Generally NO__

## Sample code:
`int *sieve = (int*) malloc(sizeof(int) * (length));`

In this example:
- void* is automatically and safely promoted to any other pointer type.
- casting adds clutter to the code and is not easy to read.
- Uses unneccessary repitition.
- It can hide errors relating to not including the correct header files.
