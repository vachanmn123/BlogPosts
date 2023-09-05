## 1. Explain the declaration, initialization and accessing the members of structure with example?

- Structures are used to store data of different types together.
- A structure is a user-defined data type in C.
- A structure creates a data type that can be used to group items of possibly different types into a single type.

### Structure Declaration:
```c
struct structure_name {
    data_type member1;
    data_type member2;
    ...
    data_type memberN;
};
```

### Structure Initialization:
```c
struct structure_name {
    data_type member1;
    data_type member2;
    ...
    data_type memberN;
} variable_name;

(OR)

struct structure_name {
    data_type member1;
    data_type member2;
    ...
    data_type memberN;
};
struct structure_name variable_name;
```

### Structure Accessing:
```c
variable_name.member_name;
```

### Example:
```c
#include <stdio.h>
#include <conio.h>

struct student {
    char name[20];
    int roll;
    float marks;
};

int main() {
    struct student s1={"ABC", 1, 90.5};
    struct student s2={"XYZ", 2, 95.5};
    printf("Name: %s\n", s1.name);
    printf("Roll: %d\n", s1.roll);
    printf("Marks: %.2f\n", s1.marks);
    printf("\n");
    printf("Name: %s\n", s2.name);
    printf("Roll: %d\n", s2.roll);
    printf("Marks: %.2f\n", s2.marks);
    getch();
    return 0;
}
```

### Output:
```
Name: ABC
Roll: 1
Marks: 90.50

Name: XYZ
Roll: 2
Marks: 95.50
```

## 2. Differentiate between structure and union?
<table>
    <th>
        <tr>
            <td><b>Structure</b></td>
            <td><b>Union</b></td>
        </tr>
    </th>
    <tr>
        <td>Defined using the `struct` keyword.</td>
        <td>Defined using the `union` keyword.</td>
    </tr>
    <tr>
        <td>Each member has its own storage location.</td>
        <td>All members share the same storage location.</td>
    </tr>
    <tr>
        <td>A user can access individual members at a given time.</td>
        <td>A user can access only one member at a given time.</td>
    </tr>
    <tr>
        <td>Syntax:
            <pre>
                struct struct_name {
                    data_type field_name1;
                    .
                    .
                    .
                } var1, var2, ...;
            </pre>
        </td>
        <td>Syntax:
            <pre>
                union union_name {
                    data_type field_name1;
                    .
                    .
                    .
                } var1, var2, ...;
            </pre>
        </td>
    </tr>
    <tr>
        <td>Altering a value doesn't affect other fields.</td>
        <td>Altering a value affects other fields.</td>
    </tr>
</table>

## 3. Write a function to perform read and write data from file.

### Program:
```c
#include <stdio.h>
#include <conio.h>

void read_file(FILE *fp) {
    char ch;
    while((ch=fgetc(fp))!=EOF) {
        printf("%c", ch);
    }
    printf("\n");
}

void write_file(FILE *fp, char *str) {
    fprintf(fp, "%s", str);
}

int main() {
    FILE *fp;
    char str[100];
    fp=fopen("file.txt", "w");
    printf("Enter a string: ");
    gets(str);
    write_file(fp, str);
    fclose(fp);
    fp=fopen("file.txt", "r");
    read_file(fp);
    fclose(fp);
    getch();
    return 0;
}
```

### Output:
```
Enter a string: Hello World!
Hello World!
```

## 4. Define Enumerated datatype. Explain the declaration and access of enumerated datatype with a code in c.

- Enumerated Data type is a user defined data type based on standard type.
- It consists of a set of named integer constants.
- The `enum` keyword is used to define an enumerated data type.
- Using the enumerated type, we can declare a variable which can store the values specified in the enumerated list. These are called enumerated variables.

### Declaration of Enumerated Data Type:

#### Syntax:
```c
enum enum_name {
    value1,
    value2,
    ...
    valueN
};
```

#### Example:
```c
enum weekday {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
};
```

### Enumerated Variable Declaration:
#### Syntax:
```c
enum enum_name variable_name;
```

#### Example:
```c
enum weekday day;
```

### Enumerated Variable Initialization:
#### Syntax:
```c
enum enum_name variable_name=value;
```

#### Example:
```c
enum weekday day=Monday;
```

### Enumerated Variable Accessing:
#### Syntax:
```c
variable_name=value;
```

#### Example:
```c
day=Monday;
```

### Program:
```c
#include <stdio.h>
#include <conio.h>

enum weekday {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
};

int main() {
    enum weekday day=Monday;
    printf("Day: %d\n", day);
    day=Tuesday;
    printf("Day: %d\n", day);
    day=Wednesday;
    printf("Day: %d\n", day);
    day=Thursday;
    printf("Day: %d\n", day);
    day=Friday;
    printf("Day: %d\n", day);
    day=Saturday;
    printf("Day: %d\n", day);
    day=Sunday;
    printf("Day: %d\n", day);
    getch();
    return 0;
}
```

### Output:
```
Day: 0
Day: 1
Day: 2
Day: 3
Day: 4
Day: 5
Day: 6
```

## 5. Write a c program to store and print student NAME, USN, branch, test marks using structure?

### Program:
```c
#include <stdio.h>
#include <conio.h>

struct Student {
    char name[20];
    char usn[20];
    char branch[20];
    float marks;
};

int main() {
    struct Student s[10];
    int n, i;
    printf("Enter the number of students: ");
    scanf("%d", &n);
    printf("\n")
    for (i=0; i < n; i++) {
        printf("Enter the details of student %d:\n", i+1);
        printf("Name: ");
        scanf("%s", s[i].name);
        printf("USN: ");
        scanf("%s", s[i].usn);
        printf("Branch: ");
        scanf("%s", s[i].branch);
        printf("Marks: ");
        scanf("%f", &s[i].marks);
        printf("\n");
    }
    printf("The details of the students are:\n");
    for (i=0; i < n; i++) {
        printf("Name: %s\n", s[i].name);
        printf("USN: %s\n", s[i].usn);
        printf("Branch: %s\n", s[i].branch);
        printf("Marks: %.2f\n", s[i].marks);
        printf("\n");
    }
    getch();
    return 0;
}
```

### Output:
```
Enter the number of students: 3

Enter the details of student 1:
Name: ABC
USN: 4BD22CB001
Branch: CSBS
Marks: 89

Enter the details of student 2:
Name: DEF
USN: 4BD22CS005
Branch: CSE
Marks: 88

Enter the details of student 3:
Name: GHI
USN: 4BD22IS089
Branch: ISE
Marks: 88

The details of the students are:
Name: ABC
USN: 4BD22CB001
Branch: CSBS
Marks: 89.00

Name: DEF
USN: 4BD22CS005
Branch: CSE
Marks: 88.00

Name: GHI
USN: 4BD22IS089
Branch: ISE
Marks: 88.00
```
