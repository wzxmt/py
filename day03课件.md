## 字典：

```python
# 字典循环： dic.keys() | dic.values() | dic.items()
for k, v in dic.items():
    print(k, v)
      
# 字典嵌套
# [1, 2, 3]
# {k1:v1, k2:v2}
info = {
    '学生们': [
        {
            'name': 'Bob',
            'age': 18,
        },
        {
            'name': 'Tom',
            'age': 18,
        }
    ],
    '老师们': [
        {
            
        },
        {
            
        }
    ],
}
for k, v in info.items():
    if k == '学生们':
        for stu in v:
            print(stu)
```

## 字符编码

重点

```python
'''
1. 什么是字符编码：将人识别的字符转换计算机能识别的01，转换的规则就是字符编码表
2. 常用的编码表：ascii、unicode、GBK、Shift_JIS、Euc-kr
3. 编码操作：编码encode()、解码decode()
'''
```

知识储备

```python
# 电脑三大核心：cpu - 内存 - 硬盘(数据的存取过程)
# 软件及python解释器读取文件过程：启动 - 读取 - 展示|解释执行
# python2环境的文件头：# coding: 编码格式
```

简介与发展

```python
'''
1. ascii - 各国编码 - 万国编码
2. 存取不一致的乱码现象
3. unicode与utf-8
'''
```

核心

```python
# 编码操作：编码encode()、解码decode()
```

py2与py3

```python
'''
# python2默认采用ascii编码表
# python3默认采用utf-8

# 在文件最上方可以通过 # encoding: 编码名来规定文件解码的编码表  -- 文件头
# 在py3以后的开发环境，所有文件采用utf-8编码存储，py3默认也是采用utf-8读取文件，所有可以省略文件头
'''
```

## 字符与字节

重点

```python
'''
1. 字节的存储方式：8个二进制位
2. 字符所占字节数：根据编码的不同，所占字节数可能不同
3. 三种格式字符串：u''、b''、r''
'''
```

了解

```python
'''
u、b格式字符串转换: str(b'', encode='utf-8')、bytes(u'', encode='utf-8')
u'' = encode('utf-8') > b''
b'' = decode('utf-8') >  u''
'''
```

```
# 乱码：存和取所采用的编码不一致

# 编码：ascii，unicode, gbk, gb2312, utf-8

# 电脑组成：硬盘 - 内存 -(二级缓存、一级缓存、cpu寄存器)- cpu

# cpu交互的是用户能识别的数据：字符
# 硬盘中最终存储的数据：0,1的二进制数据(可以直接转化为电脑能识别的高低电频)


# 什么是字符编码：将人识别的字符转换计算机能识别的01，转换的规则就是字符编码表
''' 编码表 对应关系
你好 <=> 000010001001010101
好的 <=> 001010001001010000
'''

# 最早期对应关系：ascii编码表 - 存放的是英文数字与机器二进制的对应关系
# 数字70对应ascii表，指向的是字母'F'
print(chr(70))  # 'F'
print(ord('f'))  # 102

# 字符所占字节数
# 1字节 = 8个二进制位 00000000 ~ 11111111 256个数字 -128 ~ 127

# ascii中一个字母或数字占一个字节

# 中文
# GBK： 16个二进制位 15个0到15个1
# 兼容ascii，一个字母或数字占一个字节
# 2w多汉字，用两个字节进行存储

'''
你好 <=> 00000101010101001011 <=> 콱봤
'''
# 日文/韩文：Shift_JIS、Euc-kr

# 国际上交流：
# 一条信息中，可能同时出现英文/中文/日文/韩文，将所有信息存储，且不乱码
# 万国编码表：unicode
# unicode采用两个字节存放数据：utf-8，utf-16
# utf-8采用变长存储：1字节存放数字与英文，3字节存放汉字
# utf-16采用定长存储：均以2字节存放数字，英文，汉字

# 内存中用utf-16存取数据：定长存取效率高（变长需要计算后才存取）
# cpu中与硬盘中，采用utf-8存放数据（utf-8传输更快）
```

```
# 原文本字符串数据
# s1 = 'abc123你好'
s1 = u'abc123你好'
print(s1)

# 二进制字符串数据: 数据传输是以字节为单位，要将原文字符串转换为二进制字符串机械能传输

# 编码
res = s1.encode('utf-8')
print(res)
# 解码
s2 = res.decode('utf-8')
print(s2)

ss2 = b'abc123\xe4\xbd\xa0\xe5\xa5\xbd\xe5\xa5\xbd\xe5\xa5\xbd'
print('>>', ss2.decode('utf-8'))




# 原义字符串数据
s3 = r'你好\n好的'
print(s3)

# s4 = 'D:\\nbpython周末四期\\day03\\代码\\4.三种字符串.py'
# print(s4)
s4 = r'D:\nbpython周末四期\day03\代码\4.三种字符串.py'
print(s4)
```

## 文件操作

重点

```python
'''
1. 文件操作的三步骤：打开文件 - 使用文件 - 关闭文件
2. 文件操作三要素：文件源、操作模式、编码
f = open(r'文件路径', '文件的操作模式', encoding='utf-8')
3. with语法：with open(...) as 别名, ..., open(...) as 别名: pass
4. 重点方法：read() | write() | readline() | close() | f.flush() | f.seek()
'''
```

操作模式

```python
'''
'''
主模式：
r:  文件必须存在的读
w:  文件无需存在的写，无创建，有清空再写
a:  文件无需存在的写，无创建，有在文件最后追加写

从模式：
t:  按文本字符操作数据（默认模式）
b:  按文本字节操作数据
+:  可读可写

了解：
x：新建文件写，如果文件已存在，抛异常
'''
'''
rt | wt | at == r | w | a
rb | wb | ab
rt+ | wt+ | at+ == r+ | w+ | a+
rb+ | wb+ | ab+
'''
```

操作方法

```python
'''
读：read() | readline() | readlines()
写：write() | writelines() | flush()
光标：seek() | tell()
特征：encoding | closed

了解：readable() | writable() | name 
'''
```

## 基础写

```python
# 文件操作模式：w  -- 文件不存在就新建，存在就清空
# 1.按字符进行操作
# 2.write('写入第1行\n写入第2行\n')
# 3.flush(): 将之前写入到内存中的数据刷新到硬盘中
# 4.writelines(list)：list中存放的是一条条文件内容，需要明确\n标识换行  writelines(['111\n', '222\n'])
```

## with语法

```python
# 操作系统对文件的支持权由with自动管理释放
with open('file.txt', 'r', encoding='utf-8') as f:  # 不需要明文书写f.close()
    data = f.read()
    print(data)
```

## 游标操作

```python
# 大前提：seek一定在b模式下进行操作，因为seek移动是按字节进行操作
# f.seek(偏移量，操作位置)

f.seek(5, 0)  # 从开始往后偏移5个字节
f.seek(-1, 1)  # 从当前位置向前偏移1个字节
f.seek(1, 1)  # 从当前位置向后偏移1个字节
f.seek(-5, 2)  # 从末尾向前偏移5个字节
```

## 文件的遍历

```python
# 最常用读写
with open('source', 'r', encoding='utf-8') as f1, open('target', 'w', encoding='utf-8') as f2:
    for line in f1:
        f2.write(line)
```
