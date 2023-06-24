free() is a function used alongside [[malloc()]] to unallocate designated memory.
By using dynamic allocation functions like malloc() you are taking memory into your 
own hands, this means that you need to keep track of all the addresses of allocated 
memory (in a variable of type pointer). You also need to ensure that all allocated 
memory is freed. Failure to do this will result in your programme running out of 
memory. The program could even kill itself. :(

# Prototype
`void free(void *ptr);`
`ptr`: is the address of the memory previously allocated and returned by a call to malloc.
__Rem__: [[malloc()]] returns a pointer to the allocated memory.

```c
void ,(int m0, int n1, int n2)
{
    int *t;
    int sum;

    t = malloc(sizeof(*t) * 3)
        // size of int * 3 = 6bytes
    t[0] = n0;
    t[1] = n1;
    t[2] = n2;
    sum t[0] + t[1] + t[2];
    printf("%d+%d+%d=%d\n", t[0], t[1], t[2], sum);
    free(t); // free the designated memory(allocated by malloc)
}

int main(void)
{
m(98, 402, -1024);
return (0);
}
```

