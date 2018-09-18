# 华为9月16日在线编程题

## 第一题

### 题目描述

在一个给定的字符串中找到最后一个只出现一次的字符。

### 输入描述：

一个定长的字符串，其中字符没有顺序，字符可以重复/

### 输出描述：

一个字符。最后一个只出现一次的字符；如果字符的出现次数都是大于1，则返回NULL。

### 示例：

输入：BACCAAHEFGHFF

输出：G

``` python
s = input()
s_reverse = s[::-1]
flag = False
for i in s_reverse:
    if s_reverse.count(i) == 1:
        flag = True
        print(i)
        break

if flag:
    pass
else:
    print("NULL")
```

## 第二题

### 题目描述

将一个字符串str的内容颠倒过来，并输出。str的长度不超过100个字符。 如：输入“Yes sir”，输出“seY ris”。

``` python
s = input().split(" ")
def s_reverse(s):
    s = s[::-1]
    return s

s1 = s[0]
s2 = s[1]
print(s_reverse(s1)+" "+s_reverse(s2))
```

## 第三题

### 题目描述

十进制20位数据乘法

### 输入描述：

两个不超过20位都不为0的十进制字符串

### 输出描述：

字符串相乘结果

### 示例：

输入：20000000000000000000 30000000000000000000

输出：600000000000000000000000000000000000000

### Python 代码

``` python
-*- coding:utf-8 -*-

a = input()
b = input()
print(int(a)*int(b))

# 这种程度能通过实例测试，不过还有大数乘法的解法
# 参考: https://blog.csdn.net/amusi1994/article/details/82717104

def recursive_multiply(x, y, n):
    if n==1:
        return x*y
    else:
        a = x/pow(10, n/2)
        b = x-a*pow(10, n/2)
        c = y/pow(10, n/2)
        d = y-c*pow(10, n/2)

    ac = recursive_multiply(a, c, n/2)
    bd = recursive_multiply(b, d, n/2)
    p = recursive_multiply(a+b, c+d, n/2) - ac -bd

    return ac*pow(10, n) + p*pow(10, n/2) + bd

if __name__ == '__main__':
    num1 = int(raw_input())
    num2 = int(raw_input())
    r = recursive_multiply(num1,num2,4)
    print r
```