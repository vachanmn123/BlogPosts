# Module - 3

## 1. Write a c program for swapping of two numbers using call by value and call by reference?
### Program:
```c
#include <stdio.h>
#include <conio.h>

void swap_by_value(int a, int b);
void swap_by_reference(int *a, int *b);

int main() {
    int a, b;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    printf("Before swapping by value: a = %d, b = %d\n", a, b);
    swap_by_value(a, b);
    printf("After swapping by value: a = %d, b = %d\n", a, b);
    printf("Before swapping by reference: a = %d, b = %d\n", a, b);
    swap_by_reference(&a, &b);
    printf("After swapping by reference: a = %d, b = %d\n", a, b);
    getch();
    return 0;
}

void swap_by_value(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    printf("Inside swap_by_value: a = %d, b = %d\n", a, b);
}

void swap_by_reference(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
    printf("Inside swap_by_reference: a = %d, b = %d\n", *a, *b);
}
```

### Output:
```
Enter 2 numbers: 2 5
Before swapping by value: a = 2, b = 5
Inside swap_by_value: a = 5, b = 2
After swapping by value: a = 2, b = 5
Before swapping by reference: a = 2, b = 5
Inside swap_by_reference: a = 5, b = 2
After swapping by reference: a = 5, b = 2
```

## 2. Define recursive function? Explain the working procedure of recursive function? Write a c program to compute GCD of two numbers?

### Recursive function:
A recursive function is a function that calls itself to solve a smaller version of its task until the final call is made which doesn't require a call to itself. There are 2 cases in a recursive function:
1. **Base case**: In this case, the problem is directly solved without making ant further calls to itself.
2. **Recursive case**: In this case, the problem is broken down into smaller versions of itself and the function calls itself to solve the smaller version of the problem. This continues until the base case is reached.

### Program to compute GCD of two numbers:
```c
#include <stdio.h>
#include <conio.h>

int gcd(int a, int b);

int main() {
    int a, b;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    printf("GCD of %d and %d is %d", a, b, gcd(a, b));
    getch();
    return 0;
}

int gcd(int a, int b) {
    if (a%b == 0) {
        return b;
    } else {
        return gcd(b, a%b);
    }
}
```

### Output:
```
Enter two numbers: 12 18
GCD of 12 and 18 is 6
```

## 3. Write the syntax of function declaration, function definition and function call with suitable example?

### Function declaration:
Function declaration is a statement that identifies a function with its name, return type and list of parameters. We use `;` at the end of the function declaration.

#### Syntax:
```c
return_data_type function_name(data_type var1, datatype var2, ...);
```

#### Example:
```c
int add(int a, int b);
```

### Function Definition:
The function definition consists of function header that identifies the function, followed by the function body that contains the executable code for that function.

#### Syntax:
```c
return_data_type function_name(data_type var1, datatype var2, ...) {
    // Local declaration
    statement 1;
    statement 2;
    .
    .
    .
    return (variable/expression);
}
```

#### Example:
```c
int add(int a, int b){
    int sum;
    sum = a + b;
    return sum;
}
```

### Function Call:
A function call is a statement that invokes a function. It consists of the function name followed by a list of arguments enclosed in parentheses.
- **Calling Function**: This is the function that calls another function. (main function calls add)
- **Called Function**: This is the function that is called by another function. (add function is called by main)

#### Syntax:
```c
function_name(argument1, argument2, ...);
```

#### Example:
```c
int main() {
    int a = 5, b = 10;
    int sum = add(a, b); // <-- Function call
    printf("Sum = %d", sum);
}
```

## 4. Write a c program to read N integers into an array A and find sum of even numbers, sum of odd numbers and average of all numbers using user defined function?

### Program:
```c
#include <conio.h>
#include <stdio.h>

void read_numbers(int *arr, int n);
int sum_of_even(int *arr, int n);
int sum_of_odd(int *arr, int n);
float average(int *arr, int n);

int main() {
    int arr[50], n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    read_numbers(arr, n);
    printf("Sum of even numbers = %d\n", sum_of_even(arr, n));
    printf("Sum of odd numbers = %d\n", sum_of_odd(arr, n));
    printf("Average of all numbers = %f\n", average(arr, n));
    getch();
    return 0;
}

void read_numbers(int *arr, int n) {
    int i;
    for (i=0; i < n; i++) {
        printf("Enter element %d: ", i+1);
        scanf("%d", &arr[i]);
    }
}

int sum_of_even(int *arr, int n) {
    int i, sum;
    sum = 0;
    for (i=0; i < n; i++) {
        if (arr[i] % 2 == 0) {
            sum += arr[i];
        }
    }
    return sum;
}

int sum_of_odd(int *arr, int n) {
    int i, sum;
    sum = 0;
    for (i=0; i < n; i++) {
        if (arr[i] % 2 != 0) {
            sum += arr[i];
        }
    }
    return sum;
}

float average(int *arr, int n) {
    int i, sum;
    sum = 0;
    for (i=0; i < n; i++) {
        sum += arr[i];
    }
    return (float)sum/n;
}
```

### Output:
```
Enter the number of elements: 5
Enter element 1: 1
Enter element 2: 2
Enter element 3: 3
Enter element 4: 4
Enter element 5: 5
Sum of even numbers = 6
Sum of odd numbers = 9
Average of all numbers = 3.000000
```

## 5. Define the different types of storage classes with example?
Storage classes define the scope, lifetime of variables defined within a C program.
### Syntax to declare a variable with storage class:
```c
storage_class data_type variable_name = value;
```

There are 4 storage classes in C
### 1. **Automatic**: 
- The variables declared with automatic storage class are called automatic variables.
- They can be defined using the `auto` keyword. (`auto data_type var_name;`)
- Their scope is limited to the block in which they are defined.
- They are initialized to garbage value by default.
- They are stored in RAM.
#### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    auto int x = 10;
    {
        auto int x;
        print("%d", x); // <-- Garbage value
    }
    printf("%d", x); // <-- 10
    getch();
    return 0;
}
```

#### Output:
```
3249032
10
```

### 2. Register:
- The variables declared with register storage class are called register variables.
- They can be defined using the `register` keyword. (`register data_type var_name;`)
- They are stored in CPU registers.
- They are initialized to garbage value by default.
- They are used to access the variables faster.

#### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    register int i, sum=0, n=10;
    for (i=0; i < n; i++) {
        sum += i;
    }
    printf("Sum = %d", sum);
}
```

#### Output:
```
Sum = 45
```

### 3. Static:
- The variables declared with static storage class are called static variables.
- They can be defined using the `static` keyword. (`static data_type var_name;`)
- They are initialized to 0 by default.
- They are stored in RAM.
- They are initialized only once.
- Their scope is limited to the block in which they are defined.
- Their lifetime is the entire program.

#### Example:
```c
#include <stdio.h>
#include <conio.h>

void display() {
    static int x;
    x += 10;
    printf("%d\n", x);
}

int main() {
    display(); // <-- 10
    display(); // <-- 20
    display(); // <-- 30
    getch();
    return 0;
}
```

#### Output:
```
10
20
30
```

### 4. Extern:
- The variables declared with extern storage class are called extern variables.
- They can be defined using the `extern` keyword. (`extern data_type var_name;`)
- They are initialized to 0 by default.
- They are stored in RAM.
- They are initialized only once.
- Their scope is for the entire program. They can be accessed from other files

#### Example:
```c
// File 1
#include <stdio.h>
#include <conio.h>

int x = 10;
extern void display();

int main() {
    display();
    getch();
    return 0;
}

// File 2
#include <stdio.h>

extern int x;
void display() {
    printf("%d", x);
}
```

#### Output:
```
10
```
