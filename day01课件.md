## 学习方法

```python
'''
重点：熟练度
3w1h：what | why | where | how
'''
```

## why are you here

```python
'''
1. 编程语言：与计算机进行沟通的语言
2. 编程：奴役计算机，让计算机安装指定的方式帮助我们完成特定的需求（重点）
3、编程语言：类似音乐音符形成的音谱，特点的电流谱，让没有生命的高低电流变得有生命
4、编程的目的：奴役电脑，让电脑变成我们赚钱的机器
'''
```

## 计算机语言的发展

```python
'''
1. 机器语言：01代码指令
2. 汇编语言：助记词 MOV CMP CF
3. 高级语言：java 、C、python

总结;
1.机器语言，与机器直接交互，执行效率最高
2.汇编语言，执行效率较高，没有机器语言效率高，开发效率比机器语言高
3.高级语言，执行效率最低，开发效率最高 （重点）
'''
```

## 高级语言的执行方式

```python
'''
1.编译型：类似于百度翻译，执行效率高

2.解释型：类似于同声传译，开发效率高 （python: 后出现的能使用前出现的(资源)，反过来不行）
'''
```

## python交互方式

```python
'''
1.实时交互：提前进入python解释器环境
2.文件交互：将文件交给python解释器执行（效率高）
注：python默认文件后缀为py
'''
```

## 变量

```python
'''
1. what: 可变的 状态(量是用来描述事物的某种状态)
2. why: 如何用代码来描述事物的某种（可变化的）状态
3. where: ...
4. how：
	- 如何定义变量： 变量名 = 变量值
		-- name = 'Owen'
		-- 在堆区开辟空间存放变量值，在栈区开辟名为变量名的空间存放堆区变量值那个区域的地址
		-- name = 'Egon'
		-- 重新赋值，重新开辟空间存放变量值，跟原本的变量名进行绑定，原来变量名name的值就为Egon
	- 如何使用变量： 变量名
		-- 没有被变量名绑定的变量值就会被系统回收
'''
```

## 变量三要素

```python
'''
1. 变量值：变量名

2. 变量地址：id(变量名)

3. 变量的类型：type(变量名)

注：新建值，系统就会开辟空间存放该值，但存在python的优化机制，当变量值简单时，python会沿用之前的变量值
n1 = 'Owen chen'
n2 = 'Owen chen'
正常情况(一个值开辟一个空间存放)：id(n1) != id(n2)

n1 = 'Owen'
n2 = 'Owen'
优化情况(沿用之前空间值)：id(n1) == id(n2) （了解）

思考
n1 = n2 = 'Owen chen' <=> n1 = 'Owen chen'  n2 = n1
id(n1) == id(n2)
'''
```

## 变量（标识符）命名规范（重点）

```python
'''
1. 可以由数字、字母、下划线组合
2. 不能以数字开头
3. 不能与系统关键字保留字重名
4. 见名知意，建议使用_连接语法（驼峰 owenName OwenName | _连接  owen_name），一般_开头或结尾都有特殊含义
'''
```

## 交互输入

```python
'''
变量名 = input("文本提示")

注：回车后，系统在控制台等待用户输入具体的 变量值
'''
```

## 格式化输出

#### 关键字的方式

```python
# 需要从键盘上录入三个变量值
name = input('请输入姓名：')
gender = input("请输入性别：")
age = input("""请输入年龄：""")
# 按照指定的多行文本格式输出
print("""------- name: %s -------
name：%s
gender：%s
age：%s
---------- end ----------""" % (name, name, gender, age))
# 了解：
# %s本质上是为字符串站位，但是可以为所以类型数据进行站位
# %d是数字类型占位符，只能给数字数据站位，否则报错
# %05.2f：.2代表保留2位小数，5代表输出结果最少占5位(小数点也算)，0代表不足为以0填充
print("%05.2f" % 3.1415)
```

#### 索引的方式

```python
多行字符串.format(索引0值，索引1值,索引2值)比如上面的程序就是name对应上面的所有{0}，gender对应上面的所有{1},age对应上面的所有{2}
name = input('请输入姓名：')
gender = input("请输入性别：")
age = input("""请输入年龄：""")
# 按照指定的多行文本格式输出
print("""------- name: {0} -------
name：{0}
gender：{1}
age：{2}
---------- end ----------""" .format (name,gender,age))
```

#### 键值对

```python
这种方式方式采用的是键值对的方式，在info中指定键，在设置值的时候采用键=值的形式，没有必要关心前后顺序，只要设置好就行，所以这种方式比较好
name = input('请输入姓名：')
gender = input("请输入性别：")
age = input("""请输入年龄：""")
# 按照指定的多行文本格式输出
info="""------- name: {name} -------
name：{name}
gender：{gender}
age：{age}
---------- end ----------""".format (name=name,gender=gender,age=age)
print (info)
```

#### 变量

```python
这种方式方式采用的是键值对的方式，在info中指定键，f""" {name}"""自动转换成变量
name = input('请输入姓名：')
gender = input("请输入性别：")
age = input("""请输入年龄：""")
# 按照指定的多行文本格式输出
info=f"""------- name: {name} -------
name：{name}
gender：{gender}
age：{age}
---------- end ----------"""
print (info)
```

## 数据类型

```python
'''
# int、float、str、bool、list、dict

# int
age = 18
print(age, type(age))

# float
salary = 88888.88
print(salary, type(salary))

# bool: True | False
result = False
print(result, type(result))

# list: 存放多个数据
# 教室存放学生
list_1 = ['小王', '小李', '大钱']
print(list_1, type(list_1))
# 有老师的教室存放学生
list_2 = ['小王', '小李', '大钱', True]
print(list_2, type(list_2))

# 嵌套：有老师的教室里有两个小组
list_3 = [
    ['小王', '小李'],
    ['大钱', '大张'],
    True
]
print(list_3, type(list_3))

# dict: 以key-value存储数据
dic = {
    'name': '小王',
    'age': 16,
}
print(dic, type(dic))

'''
```

## 运算符

```python
'''
# 算术运算符
print(10 + 10)

# 字符串 +(字符串拼接) *(字符串重复)
s = "Owen"
end = "！！！"
s = s + end
print(s)  # Owen！！！
# 往上找最近的s
print(s * 3)  # Owen！！！Owen！！！Owen！！！

# % 取余(求模) | **指数(求幂) | //整除  | /除法(有小数的除法)
print(5 % 2)  # 1
print(5 ** 2)  # 25
print(5 // 2)  # 2
print(5 / 2)  # 2.5

# 比较运算符
# > | < | == | != | >= | <=
res = 5 >= 3
print(res)

'''
# 判断一个值是否大于3小于5
num = input("请输入一个数:")
print(type(num))
#  讲str的num转换为int的num
num = int(num)  # 注：类型()可以完成类型转换
print(type(num))

# 可以连比
print(5 > num > 3)

# 逻辑运算符
# and | or | not
# and为真：两个真 | 为假，有一个及以上为假就为假
# or为假：两个假 | 为真，有一个及以上为真就为真
# not真真假假，假假真真
print(5 > num and num > 3)

# 数字a>10 或是 数字b<30
a = int(input("a<num>:"))
b = int(input("b<num>:"))
print(a > 10 or b < 30)
'''

# 难点(逻辑运算符的短路现象)：
# and前为假，整个表达式就为假，后面不用判断，被短路
# or前为真，整个表达式就为真，后面不用判断，被短路
res = 1 and 2 or 3
print(res)  # 2
res = 1 and 0 or 3
print(res)  # 3

res = 1 and 0 and 3
print(res)  # 0
res = 1 or 0 or 3
print(res)  # 1

# == 与 is的比较区别（要拿cmd测试）
print("10" == 10)  # False
# x = "Owen chen"
# y = "Owen chen"
# print(id(x), "---", id(y))
# print(12345678901234567890 == 12345678901234567890)

""" == 只做值比较 | is会做id比较
>>> x = "owen chen"
>>> y = "owen chen"
>>> id(x)
2239318193264
>>> id(y)
2239318193392
>>> x == y
True
>>> x is y
False
>>>
"""

print(not 1)  # False
print(not True)  # False
print(not False)  # True
print(not 0)  # True
'''
```

## 流程控制

```python
'''
顺序结构
'''
```

```python
'''
分支结构
'''
```

```python
'''
循环结构
while
案例：三次密码登录执行命令
'''
```
