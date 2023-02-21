[TOC]
- [**NO.1**](#no1)
  - [编程要求：](#编程要求)
- [**NO.2**](#no2)
  - [解压密码](#解压密码)
- [**NO.3**](#no3)
  - [审查密码](#审查密码)

## **NO.1**
### 编程要求：

1. 创建一个DataFrame将已有表格内容读出并存入此DataFrame中；
2. 添加字段sum，其值为相应学生的Python和Math两门课程分数之和；
3. 将更新过的DataFrame中的内容写回students.xlsx文件的scores工作表中。\
最后excel文件中的结果如下图所示：
![图 1](../images/2be82f9eb7d7555117c5e002ae2ecb53cb88e7cb2d0c8b504538ba9077de6afe.png)

查看excel文件的内容
```python
import pandas as pd
data = pd.read_excel(r'C:\Users\zhouyi\Desktop\data.xlsx')
print(data)
```
得到结果
```python
     NO      name  Python  Math
0  1001  xiaoming      77    87
1  1002  xiaohong      88    82
2  1003   xiaohua      99    91
```
添加新列并名为'sum',其值为Python与Math成绩之和

    data['Sum'] = data['Python'] + data['Math']

结果为

```python
     NO      name  Python  Math  Sum
0  1001  xiaoming      77    87  164
1  1002  xiaohong      88    82  170
2  1003   xiaohua      99    91  190
```
将其写进excel，利用`data.toexcel()`方法
```
data.to_excel(r'C:\Users\zhouyi\Desktop\data.xlsx',sheet_name='scores')
```
即得上述结果

## **NO.2**
### 解压密码
&emsp; 小明是一名密码学专业的学生，最近他发明了一种密码压缩的方式，如下所述：对于连续的若干个相同的子串 X 会压缩为 [DX] 的形式，比如说字符串 ABABABAB 就压缩为 [4AB]。想必你应该看懂了小明对密码的压缩方式，那么现在编写一个 Python 程序获取用户的输入，对一串被压缩的密码，进行解压缩。\
输入格式:  `AB[4DEN]`  输出格式:  `ABDENDENDENDEN`  ***用到了正则表达式***
```python
import re
code =input()
r = re.search('(?<=[A-Z][A-Z]\[)\S+(?=\])',code)
n=''
code_ = ''
for i in r.group()#得到一个字符串:
    if i in '1234567890':
        n+=i
    else:
        code_+=i
a=code.split("[")[0]
print(a+int(n)*code_)
```

## **NO.3**

### 审查密码

&emsp; 某平台为了加强用户账号的安全性，在用户设置密码时提出以下限制：密码长度必须大于等于 8 位，小于等于 16 位，密码只能由大写字母（A—Z）、小写字母（a—z）和数字（0—9）组成，并且密码中必须包含以上所有三种字符。例如，"Abc1234567890" 可以通过审查，"abc1234567890" 则不能通过审查。按照上述规则，编写一个 Python 程序，获取用户输入的密码，对用户密码的合法性进行审查，输出对应的信息。  
输入格式:  `Abc1234567890`  输出格式:  `密码审查通过`  
输入格式:  `abc1234567890`  输出格式:  `密码审查未通过`  
```python
import re
code =input()
if len(code)<8 or len(code)>16:
    print('密码审查未通过')
up = re.search('[a-z]',code)
low = re.search('[A-Z]',code)
digital = re.search('[0-9]',code)
if up and low and digital:
    print('密码审查通过')
else:
    print('密码审查未通过')

```



