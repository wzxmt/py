## 赋值运算

```python
a = 10
print(a)

# py没有定义常量的语法，但可以用全大写变量名来约定俗成常量
PI = 3.14
print(PI)
PI = 5.21
print(PI)

# 需求：交换两个整型数的值
a = 10
b = 20

# c = a
# a = b
# b = c
# print(a, b)

# 交叉赋值
# a, b = b, a
# print(a, b)

# 运算赋值
# + -...
num = 100
# num += 1  # num = num + 1
# print(num)

# num **= 2
# print(num)


# 解压赋值
list = [1, 2, 3, 4, 5]
a, b, c, d, e = list  # 按位赋值
print(a, b, e)

# 只想得到首尾两个（1，5）
x, _, _, _, y = list
print(x, y)
```

## if循环

```python
#  顺序结构
# 判断分支：根据不同的实际情况选择执行分支
# 语法：
'''
if 条件表达式:
    逻辑语句1  # 利用缩减表示附属关系
    ...
    逻辑语句n
逻辑语句n+1

'''
# part1
# if age <= 18:
#     print("去相亲!")

# print('if分支执行完毕')

# if age > 18:
#     print("阿姨好，打扰了！")


# part2
'''
if 条件表达式1:
    逻辑语句块1
else:
    逻辑语句块2
'''
# if age <= 18:
#     print("去相亲!")
# else:
#     print("阿姨好，打扰了！")


# part3
'''
if 条件表达式1:
    逻辑语句块1
elif 条件表达式2:
    逻辑语句块2
else:
    逻辑语句块3
'''
# price = int(input("phone price: "))
# if price > 15000:
#     print("不考虑！")
# elif price > 10000:  # 该分支可以有0~n个
#     print('观望！')
# else:  # 该分支也可以省略
#     print('入手！')


# 案例：登录
username = input("请输入账号：")
# owen 123
if username == 'owen':
    pwd = input("请输入密码：")
    # 账号成立后，要进一步都密码进行验证：形成if的嵌套
    if pwd == '123':
        print('登录成功')
    else:
        print('密码错误')
else:
    print("账号不存在！")
```

## while循环

```python
# 循环语法
'''
while 条件:
    代码块

# 原理：当条件为真，执行代码块，到条件为假，结束该循环
'''

# 计数器
count = 1
while count <= 5:
    print('engo最衰')
    count += 1


# break：用来结束所属的最近的一层循环
# 找1~100之间是7的倍数的最大数
res = 1
num = 1
while num <= 100:
    if num % 7 == 0:
        res = num
    num += 1
print(res)

# 从大到小循环，可以快速找到98
res = 100
num = 100
while num >= 1:
    print('====')
    # 如何达到找到第一个，就结束循环
    if num % 7 == 0:
        res = num
        break  # break当次循环的逻辑下方代码被中断屏蔽
    num -= 1
print(res)

# continue：结束本次循环(中断屏蔽当次循环的逻辑下方代码),进入下一次循环
ages = [18, 32, 20, 35, 27, 25]
# 需求：打印所有30岁以下的年龄
# count = 0
# while count < 6:
#     if ages[count] < 30:
#         print(ages[count])
#     count += 1

count = 0
while count < 6:
    if ages[count] >= 30:
        count += 1
        continue
    else:
        print(ages[count])
    count += 1

# while...else...: else为循环合理结束之后的分支（不合理：循环被break中断了）
count = 0
while count < 5:
    if count == 3:
        # count += 1
        # continue
        break
    count += 1
else:
    print("循环合理结束")
```

## 数字类型

```python
'''
1. 整型
a1 = 10
a2 = int(20)

2. 长整型(py2特有，py3废弃)
b1 = 12345678901234567890
b2 = long(100)

3. 浮点型
c1 = 3.14
c2 = float(5.12)

4. 复数类型
d = 2 + 3j
'''

'''
总结：
1. 只可以存放一个值：num = 1000
2. 为不可变类：num += 1
'''
```

## 字符串类型

```python
''' *****
1. 单行字符串
s1 = 'abc'
ss1 = "xyz"

2. 多行字符串
s2 = """first line
second line
last line"""

3. 字符串嵌套
i) 单、双、三引号直接可以相互嵌套
ii) 同类型引号直接嵌套需要转义：\'  |  \"

4. 索引取值
s4 = 'oldboy'
i) 正向取值从0开始：s4[0]
ii) 逆向取值从-1开始：s4[-1]

5. 切片(顾头不顾尾，切片有步长)
s5 = 'my love'
语法：[起始索引:结束索引:步长]
i) 步长省略，默认为1
ii) 起始索引省略，默认为从头开始
iii) 结束索引省略，默认到最后结束

了解：逆向取值，起始索引与步长为负值情况下

6. 长度
s6 = 'oldboy'
print(len(s6))
print(s6.__len__())

7. 成员运算
语法：in | not in：子字符串是否在父字符串中
'he' in 'hello'

8. 首尾去白
语法：strip()
' hello wolrd  '.strip()
'===login success==='.strip('=')

9. 拆分
语法：split(拆分规则, 拆分次数)
'D:\\python36\\python3.exe'.split('\\', 1)

10.纯数字判断
语法：isdigit()
'18'.isdigit()

11. 循环(迭代)
s10 = 'hello wolrd'

count = 0
while count < len(s10):
	print(s10[count])
	count += 1
	
for s in s10:
	print(s)
'''

'''
总结：
1. 只可以存放一个值：s = 'abc'
2. 为不可变类：s = 'xyz'
'''

'''
# 1. lstrip | rstrip：左 | 右 去留白
s1 = "  hello  world  "
print(s1.rstrip())
ss1 = "===hello  world***"
print(ss1.rstrip("*"))

# 2. rsplit：从右开始拆分
s4 = "D:\\pathon36\\python3.exe"
s4_list = s4.rsplit('\\', 1)
print(s4_list)

# 3. lower | upper：全小 | 大写
print("AbCd".lower())
print("AbCd".upper())

# 4. startswith | endswith：以某某开头 | 结尾：返回值为bool类型
print("http://www.baidu.com".startswith('https://'))
print("http://www.baidu.com".endswith('com'))  # 思考：自学正则：re

# 5. format：格式化
print('name:%s，age:%s' % ('owen', 18))
# 占位与实际数据要进行个数与位置的匹配
print('name:{}，age:{}'.format('Liuxx', 8))
# 指定位置要数据：{0}要0号位数据
print('name:{0}，age:{1}, name:{0}'.format('Linoo', 58))
# 指定名字要数据
print('name:{usr}，age:{age}, name:{usr}'.format(age=58, usr='Linoo'))

# 6. replace：替换
# 语法：replace(oldS, newS, count)
s6 = 'abcabcabc'
newS6 = s6.replace('a', 'A', 2)
print(newS6)
'''

''' *
# 1. find | rfind：查找子字符串索引，无结果返回-1
s1 = 'abcabc'
print(s1.rfind('ab'))  # 返回第一次查询到的（目标字符串首位）正向索引

# 2. index | rindex：查找子字符串索引，无结果抛出异常
# print(s1.index('cb'))  # 崩溃

# 3. count：计算子字符串个数
print(s1.count('abc'))

# 4. center | ljust | rjust | zfill：按位填充
# 语法：center(所占位数, '填充符号')
# 使用： 调用者.center(参数)
print("华丽分割线".center(30, '-'))
print("华丽分割线".ljust(30, '-'))
print("1240".zfill(5))
print("9010".zfill(5))
print("59000".zfill(5))

# 5. expandtabs：规定\t所占空格数
print('hello\tworld'.expandtabs(8))

# 6. captialize | title | swapcase：首字母大写 | 单词首字母大写 | 大小写反转
print("hello world".capitalize())
print("hello world".title())
print("hello WORLD".swapcase())

# 7. isdigit | isdecimal | isnumeric：数字判断
# s7 = b'123'  # isdigit来判断是否可以转换为数字
print(b'123'.isdigit())
# 三个方法均有
print(u'123'.isdigit())
print(u'123'.isdecimal())
print(u'123'.isnumeric())

print('肆'.isdigit())
print('肆'.isdecimal())
print('肆'.isnumeric())  # 可以判断中文数字
print('Ⅳ'.isdigit())
print('Ⅳ'.isdecimal())  # 不用管
print('Ⅳ'.isnumeric())  # 可以判断罗马数字

# 8. isalnum | isalpha：是否由字母数字组成 | 由字母组成
print('abc123_'.isalnum())
print('abc'.isalpha())

# 9. isidentifier：是否为合法变量名
print('>>>', 'a_123'.isidentifier())

# 10. islower | isupper：是否全小 | 大写
print("aBc".islower())

# 11. isspace：是否是空白字符
print(" ".isspace())

# 12. istitle：是否为单词首字母大写格式
print("Hello World".istitle())
'''

'''
了解：字符串运算
'''
```



## 列表

```python
''' *****
1. 声明：可以包含不同类型数据，可以嵌套，[]

2. 索引取值：支持正向反向

3. 切片(顾头不顾尾，切片有步长)

4. 长度

5. 成员运算

6. 增删改
list = [1, 2, 3, 4, 5]
增：append(obj) | insert(index, obj)
删：remove(obj) | del(list[index]) | pop(index)
改：list[index] = newObj

7. 循环

8. 反转
语法：reverse()

9. 排序
语法：sort(reverse=True)

'''

'''
总结：
1. 可以存放多个值：list = [1, 2, 3]
2. 为可变类型：list.append(4)
3. 有序存储：排列的索引取值
'''

''' ***
1. copy：复制

2. clear：清空

3. count：计算成员个数

4. extend：添加多个值(参数为可迭代对象)

5. index：查找索引
'''

'''
了解：列表的运算
'''
```



## 元组

```python
'''
1. 声明：可以包含不同类型数据，可以嵌套，()

2. 索引取值：支持正向反向
'''

'''
总结：
1. 可以存放多个值：t = (1, 2, 3)
2. 为不可变类型
3. 有序存储：排列的索引取值
'''
```



## 字典

```python
'''
1. 声明：key为不可变类型数据，value可以为任意类型，{}
d1 = {'name': 'Owen'}
d2 = dict(name='Owen')
d3 = dict([('name','Owen')])
d4 = {}.fromkeys(['name'], None)

2. 增删改查
增：d2['newKey'] = value
删：pop('key', defalutValue)
改：d2['key'] = newValue
查：d1['key']
了解：popitem()：从末尾开始删除，返回(key, value)

3. 长度：len

4. 成员运算：in | not in

5. 循环
i) 直接for循环
ii) keys()
iii) values()
iv) items()

6. 默认值取值：get
语法：get(key, defalutValue)

7. 更新
{'name': 'owen'}.update({'name': 'Owen', age: 18})

8. 设置默认
语法：setdefault(key, defalutValue)
'''

'''
总结：
1. 可以存放多个值：dic = {'name': 'Owen', age: 18}
2. 为不可变类型
3. 无序存储：安装key取值
'''
```



## 集合

```python
'''
1. 声明：
s = {1, 2, 3, 4, 5}

2. 集合运算
&交集 | |合集 | ^对称差集 | -差集 | 比较
'''
```

