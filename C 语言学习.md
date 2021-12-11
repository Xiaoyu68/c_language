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

