## 1. Define string? Explain any two operations on string with pseudocode?
- A string is a sequence of characters terminated by a null character (\0)
- In C, a string is a 1-D array of characters and an array of characters is a string.

### String Declaration:
```c
char string[size] = "string";
```

### String Operations:
## 1. **String Length**: The length of a string is the number of characters in it excluding the null character.
#### Program:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    char string[20] = "Hello World";
    int length = 0;
    while (string[length] != '\0') {
        length++;
    }
    printf("Length of string = %d", length);
    getch();
    return 0;
}
```
#### Output: 
```Length of string = 11```

In the program, we define a string and initialize it with the value "Hello World". Then, we use a while loop to iterate through the string and increment the value of length variable until we reach the null character. Inside the loop, we increment the value of length by 1 for each iteration. Finally, we print the value of length which is the length of the string.

## 2. **String Concatenation**: String concatenation is the operation of joining two strings together.
#### Program:
```c
#include <stdio.h>
#include <conio.h>
int main() {
    char string1[20] = "Hello";
    char string2[20] = " World";
    int i;
    int lengths1 = strlen(string1);
    int lengths2 = strlen(string2);
    for (i = 0; i < lengths2; i++) {
        string1[lengths1 + i] = string2[i];
    }
    printf("String after concatenation = %s", string1);
    getch();
    return 0;
}
```
#### Output: 
```String after concatenation = Hello World```

In the program, we define two strings string1 and string2. Then, we find the length of both the strings using strlen() function. Next, we use a for loop to iterate through the second string and copy its characters to the end of the first string. Finally, we print the value of string1 which is the concatenated string.

## 2. Write a c program to replace each constant in a string with the next one except letter "z" "Z" and "a" "A". Thus the string "programming in C" should be modified as "Qsphsannjohjo D".

#### Program:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    char string[100];
    int i;
    printf("Enter a string: ");
    gets(string);
    for (i = 0; string[i] != '\0'; i++) {
        if (string[i] == 'z') {
            string[i] = 'a';
        } else if (string[i] == 'Z') {
            string[i] = 'A';
        } else if ((string[i] >= 'a' && string[i] < 'z') || (string[i] >= 'A' && string[i] < 'Z')) {
            string[i] = string[i] + 1;
        }
    }
    printf("String after replacing constants: %s", string);
    getch();
    return 0;
}
```

#### Output:
```
Enter a string: programming in C
String after replacing constants: Qsphsannjohjo D
```

## 3. Discuss the working of following string manipulation function with suitable code. (i)strchr() (ii)strcmp() (iii)strcpy() (iv)strcspn()

### (i) strchr():
- The strchr() function returns a pointer to the first occurrence of the character ch in the string str.
- If the character is not found, it returns a null pointer.

#### Syntax: 
```c
char *strchr(const char *str, int ch)
```

#### Example:
```c
#include <conio.h>
#include <stdio.h>

int main() {
    char string[20] = "Hello World";
    char *pointer;
    pointer = strchr(string, 'W');
    printf("String starting from W is: %s", pointer);
    getch();
    return 0;
}
```

#### Output:
```String starting from W is: World```

### (ii) strcmp():
- The strcmp() function compares two strings character by character.
- If the first character of two strings is equal, the next character of two strings are compared.
- This process continues until the corresponding characters of two strings are different or a null character is reached.
- If the corresponding characters of two strings are different, the strcmp() function returns the difference between the ASCII values of the characters.

#### Syntax: 
```c
int strcmp(const char *str1, const char *str2)
```

#### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    char string1[20] = "Hello World";
    char string2[20] = "Hello World";
    int result;
    result = strcmp(string1, string2);
    if (result == 0) {
        printf("Strings are equal");
    } else {
        printf("Strings are not equal");
    }
    getch();
    return 0;
}
```

#### Output:
```Strings are equal```

### (iii) strcpy():
- The strcpy() function copies the string pointed by source (including the null character) to the destination.
- The strcpy() function returns the destination string.

#### Syntax: 
```c
char *strcpy(char *destination, const char *source)
```

#### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    char string1[20] = "Hello World";
    char string2[20];
    strcpy(string2, string1);
    printf("String 1: %s\n", string1);
    printf("String 2: %s", string2);
    getch();
    return 0;
}
```

#### Output:
```
String 1: Hello World
String 2: Hello World
```

### (iv) strcspn():
- The strcspn() function returns the number of characters in the initial segment of str1 which are not in the string str2.
- If the first character of str1 is found in str2, the function returns 0.

#### Syntax: 
```c
size_t strcspn(const char *str1, const char *str2)
```

#### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    char string1[20] = "Hello World";
    char string2[20] = "World";
    int result;
    result = strcspn(string1, string2);
    printf("Number of characters: %d", result);
    getch();
    return 0;
}
```

#### Output:
```Number of characters: 6```

## 4. Explain with an example, how an array of strings is stored in main memory?   
- An array of strings is stored in main memory as a 2-D array of characters.
- Each row of the array represents a string and the columns represent the characters of the string.
- The last character of each row is the null character (\0) which indicates the end of the string.

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| a | b | c | d | \0 |
| e | f | g | h | \0 |
| a | t | b | a | \0 |

## 5. Define pointer? Explain pointer variable declaration and initialization with suitable code?
- A pointer is a variable that stores the address of another variable.
- A pointer variable points to a data type (like int or char) of the same type.
- It is created with the * operator.

### Pointer Declaration:
```c
data_type *pointer;
```

### Pointer Initialization:
```c
data_type *pointer = &variable;
```

### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    int number = 10;
    int *pointer;
    pointer = &number;
    *pointer = 20;
    printf("Number = %d", number);
    getch();
    return 0;
}
```

### Output:
```Number = 20```

## 6. Discuss pointer arithmetic with suitable code?
- Pointer arithmetic is the arithmetic operations on pointers.
- Pointers variables can also be used in arithmetic expressions.

### Example:
```c
#include <stdio.h>
#include <conio.h>

int main() {
    int num1 = 2, num2 = 5, sum = 0, mul, div;
    int *p1, *p2;
    p1 = &num1;
    p2 = &num2;
    sum = *p1 + *p2;
    mul = *p1 * *p2;
    div = *p2 / *p1;
    printf("Sum = %d\n", sum);
    printf("Multiplication = %d\n", mul);
    printf("Division = %d", div);
}
```

### Output:
```
Sum = 7
Multiplication = 10
Division = 2
```

## 7. Write the result of the following.
```c
int main() {
    int num1=10,num2=20;
    int *p=&num1,*q=&num2; 
    *p++=*q++; 
    printf(“%d%d”,num1,num2);
}
```

### Output:
```2020```
