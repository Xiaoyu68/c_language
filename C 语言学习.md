# C 语言学习

学习自密歇根大学CS201；主要作为基础知识回顾，查缺补漏，故不作详细笔记

### Lesson 1

Linux commend line review:

1. "~"代表跟路径用户

```shell
~/app
/User/xiaoyudeng/app
```

2. man意为查看命令详细文档

```shell
man ls
```

3. &指的是程序跑在后台

```shell
emacs app.c&
```

4. Jobs列出所有的后台任务

```shell
jobs
```

### Lesson 2

1. C语言的type

- int 4byte
- float 4byte
- double 8byte
- char 1byte

2. 所有的变量都要在使用之前提前声明
3. C语言的命名规范

- 要用字母开头
- 最长31个字符
- 不能使用c语言关键词

4. C语言的描述符

- %s: string
- $d: decimal
- %e: floating point exponent
- %f: floating point decimal
- %u: unsigned integer
- and others

5. scanf类似于printf，并且要用&

```shell
scanf("%d, %f", &a, &b)
lf是指double
```

### Lesson 7

- 平常计算机的32位/64位指的是内存地址

### Lesson 8

- An array is a "Chunk of memory"

An array is a contiguous piece of memory that can contain multiple values

- 在c语言中定义常量：#define MAX_NUM

- SumValues(int[])

里面[]指的是，定义的是array，并且是引用传递

- 选择排序

```c
void SortArray(double array[], int size) {
  int i, j, min;
  for (i = 0, i < size - 1; i++) {
    min = i;
    for (j = i + 1; j < size - 1; j++) {
      if (array[j] < array[min]) {
        min = j;
      }
    }
    
    swap(&array[i], &array[min]);
  }
}
```

### Lesson 9

- string用‘/0’来标记string的结尾，因此不需要在函数中传递size的变量
- 初始化一个string

```c
char myStr[5] = {'a', 'b', 'c', 'd', 0}; //这里0指的是'\0'
printf("myStr is %s\n", myStr);
// 疑问：所以怎么算mystr的长度？

char myStr[10]=“birdbath”; // ok to use assignment only to initialize string
printf("myStr is %s\n", myStr);

char myStr[]=“birdbath”; // better way
printf("myStr is %s\n", myStr);

printf("%c is char\n", myStr[0]);
```

- scanf

```c
// scanf只会读到第一个white space,而忽略后面的字符
char myStr[10];
printf (“Enter a string: “);
scanf(“%s”, myStr);
printf( You “ entered entered %s\n\n”, myStr)
// Enter a string: CSE 90
// You entered CSE
  
// Use %[width]s to copy only up to a maximum number of character. But, does not append the ‘\0’
char myStr[10];
printf (“Enter a string: “);
scanf(“%9s”, myStr);
myStr[9] = ‘\0 ;’ /* Do this yourself yourself just in case */
printf(“You entered %s\n\n”, myStr)
```

- getchar

```c
char myChar;
printf(“Enter a character: “);
myChar = getchar();
printf(“You entered %c\n\n”, myChar);
```

- fgets 可以读到一整行，自动加上'\0'

```c
#include<stdio.h>
#include<string.h>
int main ()
{
int inputLength=20
int cnt=0;
char str1[20], str2[20];
printf("\nEnter a string: "); // this is a string
fgets(str1, inputLength, stdin);
Make sure you’re clear the
difference between fgets
and scanf g ( , p g , ); printf("You entered %s\n",str1); //this
printf(“Enter another string: ");
scanf("%s",str2);
and scanf
printf("You entered %s\n",str2);
}
       
```

- String manipulation functions
- - Strcpy-copies a string; safer version of string copy, strncpy
  - Strcat-concatenates two strings
  - Strlen-returns the length of a string
  - Strcmp-compares two strings

### Lesson 11

- Array name is a pointer to the first element of the array

- Array indexing

```c
int list[] = {1,2,3,4}
list[2] == *(list + 2)
// when we add to a pointer, we don't literally add 1 to the pointer address
// instead we add one "address" to the pointer
  
// *(list + 1) references the next element in the array 
// be careful *(++ list) works too but now we lost our pointer to the beginning of the array 
```

- sizeof() returns the number of bytes needed to store the type

### Lesson 12

- 程序编译的步骤：

- - preprocessor 从c source file 变expanded c code (gcc –E code.c > code.i )

  ​        Removes preprocessor directives(比如#)

  - compiler 从expanded c code变 machine code .o文件 (gcc –o code.o –c code.i)
  - linker 从machine code变executable + library file (gcc –lm –o code code.o)

  ​        Produces the code binary by linking with the math library (‐lm)

- What is a Makefile?

A make file is used with the make utility to determine which portions of a program to compile 

It is basically a script that guides the make utility to choose the appropriate program files that are to be compiled and linked together

### Lesson 13

You can pass a struct to a function. All the elements are copied, If an element is a pointer, the pointer is copied but not what it points to!

关于struct的size，因为机器分配内存，四个bytes为一组，所以偶尔会有未填满的空间

If malloc’ed memory is not free’ed, then the OS will “leak memory”

This means that memory is allocated to the program but not returned to the OS when it is finished using it

The program program therefore therefore grows larger over time.