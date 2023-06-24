Used to dynamically allocate memory for an array of elements. It stands for 
contrigous allocation. It initializes the allocated memory to zero or NULL value.  
  
# Syntax:  
void* calloc(size_t num_elements, size_t element_size);  
  
- num_elements: number of elements to allocate 
- element_size: size of each element in bytes
- total amount of allocated memory = num_elements * element_size

calloc() will return a pointer to the allocated memory  
OR  
a null pointer (Usually due to insufficient memory)

# Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *numbers;
    int num_elements = 5;

    numbers = (int*)calloc(num_elements, sizeof(int));
    if (numbers == NULL) {
        printf("Memory allocation failed. Exiting...\n");
        exit(1);
    }

    printf("Enter %d numbers:\n", num_elements);
    for (int i = 0; i < num_elements; i++) {
        scanf("%d", &numbers[i]);
    }

    printf("You entered: ");
    for (int i = 0; i < num_elements; i++) {
        printf("%d ", numbers[i]);
    }

    free(numbers);  // Remember to free the allocated memory

    return 0;
}
```
