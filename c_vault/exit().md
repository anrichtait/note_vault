exit() is used to terminate a program's execution and return control to the operating system.  
  
# Tasks performed before terminating the program:
1. Flushes all output streams and closes open files.
2. It calles the functions registered by 'atexit()' in reverse order of their registration.
3. Returns control to the operating system and provides an exit value. (Number inside parens)

# Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int num;

    printf("Enter a positive number: ");
    scanf("%d", &num);

    if (num <= 0) {
        printf("Invalid input. Exiting...\n");
        exit(1);  // Terminate the program with a non-zero status
    }

    printf("The number is: %d\n", num);

    return 0;
}
```
