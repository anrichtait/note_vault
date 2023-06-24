---
id: "pointers"
aliases:
  - "Definition: Pointer or pointer variable"
tags: []
---

# Definition: Pointer or pointer variable
A memory cell that store the address of a data item.

# Syntax:
`type *variable;`

So the declaration:
`float *p;`
identifies p as a pointer variable of type "pointer to float". This means that any 
data with the float data type can be stored via memory in variable p.

The declaration statements:
```c
int m = 25;
int *itemp; //pointer to an integer
itemp = &m; //stores the address of 'm' in 'itemp'(pointer)
```
Therefore itemp -> m

# Using pointers:

## Indirection: 
The indirection operator '\*' is used to access the value stored at the memory 
address pointed to by a pointer.
Example:  
```c
int num = 10;
int *ptr = &num;    //ptr now holds the address of num
int value = *ptr;   //value is now 10
```
__NOTE!__ Pointer operators:
'\*' Operator = Indirection or dereference operator:
Used to access the value stored at a memory address pointed to. (By a pointer), 
So if ptr is a pointer variable '\*ptr' refers to the value stored at the memory 
address held by ptr.

'&' Operator = Address of operator:
Used to get the memory address of a variable.
So if var is a variable &var gives the memory address where the variable is stored.

## Memory allocation:
Pointers are often used with dynamic memory allocation functions like [[malloc()]].

Example:
```c
ptr = (int *) malloc (size * sizeof(int));
```
This basically creates an array of the size: size *sizeof(int).

## Passing by reference:
Allows functions to modify variables in the calling function by passing the variable's 
address. This is achieved by passing the memory address of the variable as an argument 
to the function.

Example:
```c
void increment (int *num)
{
    (*num)++;   //affects the original value.
}

int main(void)
{
    int value = 5;

    increment(&value);  //Pass the address of 'value'

    printf("%d\n", value);
    return (0);
}
```
Output: 6

## Data structures:
Pointers are crucial when developing complex data structures liked linked lists
, trees and graphs.

## Array Access:
[[arrays]] are closley linked to pointers in C.

### [[pointer_arithmetic]]:
Allows us to perform arithmetic operations on pointers.

# Pointers and [[functions]] arguments:
In C arguments are passed by value, this means that the called function cannot 
change the value of a variable in the calling function.

Example:
A sorting routine might exchange two out-of-order elements via a function called 
swap. In this scenario calling swap() with:

`swap(a, b);`
where the swap function is defined as:
```c
void swap(int x, int y)
{
    int temp;
    
    temp =x;
    x = y;
    y = temp;
}
```
Is not sufficient. This will only swap copies of a and b. 

In this case we need to pass 'a' and 'b' as pointers for their original values 
to be changed.
`swap(&a, &b);`

Since the operator & produces the address of a vairable &a is then a pointer to a.
In the passing of the variables a and b inside the swap function's parameters the 
parameters are declared as pointers.

Pointer arguments enable a function to access and change objects in the functio 
that called it.

Example: The following loops fills an array with integers by calls to getint:
```c
int n, array[size], getint(int *);

for (n = 0; n < size && getint(&array[n]) != EOF; n++);
```

Each call sets array[n] to the next integer found in the input and increments n.
Without passing the array's address there in no way for getint() to communicate 
the converted integer back to the caller function.

# Pointers and arrays:

Any operation that can be achieved by array subscriting can also be done with pointers.
The pointer version will in general be faster. 

`int a[10];`
Defines an array of 10 integers -> a block of 10 consecutive objects named a[0] - a[9].
Therefore a[i] will refer to the i-th integer in the array.

`int *pa;` <- pointer to integer  
`pa = &a[0];` <- Sets pa to element zero, so pa now contains the address of a[0]  
Therefore `x = *pa;` copies the contents of a[0] into x.

If pa points to a[0] then pa+1 wil lpoint to the next element -> a[1].  

Therefore `*(pa+1)` refers to the contents of a[1], pa+1 is the address and `*(pa+1)` 
is the contents of a[i].  
  
pa  -> a[0]  
pa+1 -> a[1]  
pa+2 -> a[2]  

__DEF__: the value of a variable or expression of type array is the address of the first element 'a[0]'.

Therefore pa = &a[0]; -> pa and a have identical values.  
Since the name of the array is a synonym for the location of the initial element, the assignment:  
`pa = &a[0]` is equal to saying `pa=a`.

Considering that we can then say:  
`a[i] == *(a+i)`  
`&a[i] == a+i`  
`pa[i] == *(pa+i)`

Keep in mind that:  
a pointer is a variable so pa=a and pa++ are fine  
BUT  
an array name is note a variable, so a=pa and pa++ are illegal  

__In short__: array indexing and pointer arithmetic can achieve the same result 
in accessing elements of an array. This equivalence is useful in scenarios where 
we want to manipulate arrays using pointers or perform pointer arithmetic for various 
purposes.

When an array name is passed to a functio the location of the first element is passed. 
This becomes a lcoal variable inside the called function so an array name parameter 
is essentially a pointer (a variable containing an address.)
