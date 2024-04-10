# 输出格式
```
print("我喜欢%s,%s天%.2f时"%('你',32,125.158))
>>> 我喜欢你,32天125.16时
print('我喜欢{},{:d}天{:.2f}时'.format('你',32,123.158))
>>> 我喜欢你,32天125.16时
print('{:0>5}'.format('33'))#一共填充5个数字
>>> 00033
```
### format
format格式化（将n按x格式化赋给a），(#：保留进制前缀)
a=format(n,‘格式’)#格式只能小写
format(18, ‘b’)#二进制
format(18, ‘#b’)#二进制
format(18, ‘x’)#16
format(18, ‘o’)#8
```
a=format(18, 'b')
b=format(18, '#b')
c=format(18, 'x')
d=format(18, 'o')
print(a,b,c,d)
>>> 10010 0b10010 12 22
```


# python模块：
## statistics模块
```
import statistics
1、statistics.mean()  求算术平均值
2、statistics.median() 计算数据的中位数，如果有两个中位数，则返回其平均值
   statistics.median_low() 数据中的低中位数
   statistics.median_high() 数据中的高中位数
3、statistics.mode()  计算众数
4、statistics.pvariance() 计算数据的总体方差
......

```
## collections模块
***collections模块实现了特定目标的容器，以提供Python标准内建容器dict ,list , set , 和tuple的替代选择。***
### 双向队列-deque
相对于list在动态增长方面速度更快
函数|描述
--|--
append(x)|添加 x 到右端
appendleft(x)|添加 x 到左端
clear()|移除所有元素，使其长度为0
copy(x)|创建一份浅拷贝
count(x)|计算 deque 中元素等于 x 的个数
extend(x)|扩展deque的右侧，通过添加iterable参数中的元素
extendleft(x)|扩展deque的左侧，通过添加iterable参数中的元素
index(x)|返回 x 在 deque 中的位置（在索引 start 之后，索引 stop 之前）, 返回第一个匹配项，如果未找到则引发 ValueError
insert(i,x)|在位置 i 插入 x 
pop()|移去并且返回一个元素，deque 最右侧的那一个, 如果没有元素的话，就引发一个 IndexError
popleft()|移去并且返回一个元素，deque 最左侧的那一个, 如果没有元素的话，就引发 IndexError
remove(value)|移除找到的第一个 value,如果没有的话就引发 ValueError
reverse()|将deque逆序排列
rotate(n)|向右循环移动 n 步,如果 n 是负数，就向左循环
```
a = deque('abc')
b = deque('cd')
a.extend(b)
deque(['a', 'b', 'c', 'c', 'd'])
#与append 的区别
a = deque('abc')
b = deque('cd')
a.append(b)
deque(['a', 'b', 'c', deque(['c', 'd'])])
```
### 计数器-Counter
可以支持方便、快速的计数，将元素数量统计，然后计数并返回一个字典，键为元素，值为元素个数
```
# 使用Counter方法来统计每个单词的频数
words=['remove', 'an', 'existing', 'key', 'one', 'level', 'down', 'remove', 'an',]
c=collections.Counter(words)
print(dict(c))
>>> {'remove': 2, 'an': 2, 'existing': 1, 'key': 1, 'one': 1, 'level': 1, 'down': 1}
# 使用most_common()来进行统计
Counter(words).most_common(4)# 设置为4代表取出频数前4的单词
```

## datetime库

datetime库，这也是Python最厉害的库之一，相比C++来说，是Python很大的优势，（C++处理日期问题非常麻烦）
date表示日期，time表示一天中的时分秒
datetime.dateime：日期和时间表示的类，功能覆盖date和time类。
```
import datetime
now = datetime.datetime(2024,4,10,15,4,4)
print("年为：",now.year)
print("月为：",now.month)
print("日为：",now.day)
print("小时为：",now.hour)
print("分钟为：",now.minute)
print("秒数为：",now.second)
print('当前日期为:', now.date() )
print('当前时间:', now.time() )
print("返回struct_time为",now.timetuple())   #  和date一样
print("返回UTC的struct_time为",now.utctimetuple())
print("返回的公历序列数为：",now.toordinal())   #  和date一样
print("返回标准日期格式为：",now.isoformat())   #  和date一样
print("返回的周几(1表示周一)：",now.isoweekday())    #  和date一样
print("返回的周几(0表示周一)：",now.weekday())    #  和date一样  
print("now.isocalendar():", now.isocalendar())  #  和date一样
print("now.ctime():",now.ctime())   #  和date一样
print("格式化时间为：",now.strftime('%Y/%m/%d %H:%M:%S'))   #  把日期按照format指定的格式进行格式化
print(datetime.datetime.strptime("2024/04/10 15:04:04",'%Y/%m/%d %H:%M:%S'))     #   将字符串格式转换为日期格式
>>> 年为： 2024
>>> 月为： 4
>>> 日为： 10
>>> 小时为： 15
>>> 分钟为： 4
>>> 秒数为： 4
>>> 当前日期为: 2024-04-10
>>> 当前时间: 15:04:04
>>> 返回struct_time为 time.struct_time(tm_year=2024, tm_mon=4, tm_mday=10, tm_hour=15, tm_min=4, tm_sec=4, tm_wday=2, tm_yday=101, tm_isdst=-1)
>>> 返回UTC的struct_time为 time.struct_time(tm_year=2024, tm_mon=4, tm_mday=10, tm_hour=15, tm_min=4, tm_sec=4, tm_wday=2, tm_yday=101, tm_isdst=0)
>>> 返回的公历序列数为： 738986
>>> 返回标准日期格式为： 2024-04-10T15:04:04
>>> 返回的周几(1表示周一)： 3
>>> 返回的周几(0表示周一)： 2
>>> now.isocalendar(): datetime.IsoCalendarDate(year=2024, week=15, weekday=3)
>>> now.ctime(): Wed Apr 10 15:04:04 2024
>>> 格式化时间为： 2024/04/10 15:04:04
>>> 2024-04-10 15:04:04
```
datetime.timedelta： 与时间间隔有关的类。
```
now = datetime.date.today()
before_date = now + datetime.timedelta(days=-500)
print("now date is:",now)   # 表示现在的日期
print("date before is:",before_date)   # 表示500天前的日期
>>> now date is: 2024-04-10
>>> date before is: 2022-11-27 
```

# 整数补零
有一些不同位数的数字，比如1、22、333、4444，正常作为数字或转字符串输出可能位数不一样，某些时候输出到文本在后续处理会带来麻烦。如果想保证位数一样，在前面补0。
操作非常简单，只要用s = '%04d' % n转成字符串就可。

# 将输入转换成整数
N,M,K,T=map(int,input().split())#map()是 Python 内置的高阶函数，它接收一个函数 f 和一个 list，并通过把函数 f 依次作用在 list 的每个元素上，得到一个新的 list 并返回
growtime=list(map(int,input().split()))#map()的返回值已经不再是list,而是iterators, 所以想要使用，只用将iterator 转换成list 即可， 比如 list(map()) 。
growtime.insert(0, 0)#从1号位置开始
existeed=list(map(int,input().split()))#已有的种子
relation=[list(map(int,input().split())) for i in range(K)]

# 数学函数

## 4个常数数字
常数       | 数学表示| 描述
-----------|----| --------|
math.pi	    |π	|圆周率，值为3.141592653589793
math.e	    |e	|自然对数，值为2.718281828459045
math.inf	|∞	|正无穷大，负无穷大为-math.inf
math.nan    |	|	非浮点数标记，NAN（Not a Number）
## 数值表示函数
函数| 描述
---|---|
math.fabs(x)| 返回x的绝对值
math.factorial(x)| 返回x的阶乘，如果x是小数或负数，返回ValueError
math.gcd(a,b)| 返回a与b的最大公约数
math.pow(a,b)|返回a的b次方
math.sqrt(x)|返回x的平方根

## inf
float('inf') 表示正无穷
-float('inf') 或 float('-inf') 表示负无穷

# 排列组合
```
itertools.permutations
排列，与下文的组合形成数学中的排列组合
x = itertools.permutations(range(3),2)
print(list(x))
[(0, 1), (0, 2), (1, 0), (1, 2), (2, 0), (2, 1)]
```
```
itertools.combinations
组合：元素不重复
x = itertools.combinations(range(3),2)
print(list(x))
[(0, 1), (0, 2), (1, 2)]
```
```
itertools.combinations_with_replacement
组合：允许元素重复
x = itertools.combinations_with_replacement(range(3),2)
print(list(x))
[(0, 0), (0, 1), (0, 2), (1, 1), (1, 2), (2, 2)]
```

# bisect库

二分库，Python和C++一样，系统内置了一个二分查找库，且功能非常强大。
一般就会使用两个
```
bisect_left(nums, tgt, lo=0, hi=len(nums))
bisect_right(nums, tgt, lo=0, hi=len(nums))
bisect(nums, tgt, lo=0, hi=len(nums))
bisect = bisect_right
```
bisect_left就是找第一个大于等于key的值，而bisect和bisect_right就是找第一个大于key的值

# 回溯法
```
res = []
path = []

def backtrack(未探索区域, res, path):
    if path 满足条件:
        res.add(path) # 深度拷贝
        #可以使用res.append(path[:])或者res.append(copy.deepcopy(path))
        # 但是直接res.append(path)是浅拷贝，res会随着path改变而变化
        # return  # 如果不用继续搜索需要 return
    for 选择 in 未探索区域当前可能的选择:
        if 当前选择符合要求:
            path.add(当前选择)
            backtrack(新的未探索区域, res, path)
            path.pop()
```
# 几个常用数据类型

## str
1. 切片访问 ```str_name[strat : end : step]```，左闭右开
2. 确定在一个字符串中，是否存在相同的字符或者子字符串，可以使用成员运算符中的 ```in``` 和 ```not in ```关键字
3. 字符串```+```连接(合并),```*```复制(重复)
4. 支持格式化字符串的输出，与C语言```printf()```一样用法
##### 内置方法
1. **```string.capitalize()```**:将字符串的第一个字母变成大写，其他字母变小写
2. **```string.casefold()```**:返回一个字符串，其中所有字符均为小写
3. **```string.lower()```**:转换字符串中所有大写字符为小写（符号和数字将被忽略）
4. **```string.islower()```**:检测字符串是否都由小写字母组成
5. **```string.upper()```**:将字符串中的小写字母转为大写字母（符号和数字将被忽略）
6. **```string.isupper()```**:检测字符串是否都由大写字母组成
7. **```string.title()```**:所有单词的首个字母转化为大写，其余字母均为小写
8. **```string.istitle()```**:检测字符串中所有的单词拼写首字母是否为大写，且其他字母为小写
9. **```string.swapcase()```**:将大写字母转换为小写字母，小写字母会转换为大写字母
10. **```string.count(value, start, end)```**:统计字符串里某个字符出现的次数。可选参数为在字符串搜索的开始与结束位置
11. **```string.find(value, start, end)```**:检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1
12. **```string.find(value, start, end)```**:检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1
13. **```string.find(value, start, end)```**:
* 检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1。
* index() 方法与 find() 方法几乎相同，唯一的区别是，如果找不到该值，index() 方法将引发异常，则 find() 方法将返回 -1
* ```rfind()、rindex()```，从右搜索并返回
14. **```string.startswith(value, start, end)```**:检查字符串是否是以指定子字符串开头，如果是则返回 True，否则返回 False
15. **```string.endswith(value, start, end)```**:判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回 True，否则返回 False
16. **```string.isalnum()```**:检测字符串是否由字母和数字组成
17. **```string.isalpha()```**:检测字符串是否只由字母或文字组成
18. **```string.isdigit()```**:检测字符串是否只由数字组成
19. **```string.split(separator, max)```**:通过指定分隔符从左侧对字符串进行切片，默认值为空白字符;如果第二个参数 num 有指定值，则分割为 num+1 个子字符串,默认值为 -1，即“所有出现次数”
20. **``string.join(iterable)```**:将序列中的元素以指定的字符连接生成一个新的字符串,所有返回值均为字符串的任何可迭代对象
21. **```string.replace(oldvalue, newvalue, count)```**:把字符串中的 old（旧字符串） 替换成 new(新字符串)，如果指定第三个参数max，则替换不超过 max 次

## list
1. **```del list_name[i]```** 来删除某个指定元素，其中 list_name 表示列表名，i 表示指定值的索引值
2. **```list.append(element)```**:用于在列表末尾添加新的对象
3. **```list.insert(position, element)```**:用于将指定对象插入列表的指定位置
4. **```list.extend(iterable)```**:用于在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）,iterable-任何可迭代对象（列表、集合、元组等）
5. **```list.count(value)```**:用于统计某个元素在列表中出现的次数
6. **```list.index(element)```**:用于从列表中找出某个值第一个匹配项的索引位置
7. **```list.sort(reverse=True|False, key=myFunc)```**:用于对原列表进行排序，如果指定参数，则使用比较函数指定的比较函数,reverse=True 将对列表进行降序排序。默认是 reverse=False。
key	可选,指定排序标准的函数。
```
# 返回值的长度的函数：
def myfunc(e):
    return len(e)
words = ['aa', 'b', 'ccc', 'dddd']
words.sort(reverse=True, key=myfunc)
print(words)
>>> ['dddd', 'ccc', 'aa', 'b']
```
8. **```list.copy()```**:copy() 方法用于复制列表，类似于 a[:]
9. **```string.swapcase()```**:将大写字母转换为小写字母，小写字母会转换为大写字母
10. **```string.count(value, start, end)```**:统计字符串里某个字符出现的次数。可选参数为在字符串搜索的开始与结束位置
11. **```string.find(value, start, end)```**:检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1
12. **```string.find(value, start, end)```**:检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1
13. **```string.find(value, start, end)```**:
* 检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回 -1。
* index() 方法与 find() 方法几乎相同，唯一的区别是，如果找不到该值，index() 方法将引发异常，则 find() 方法将返回 -1
* ```rfind()、rindex()```，从右搜索并返回
1.  **```string.startswith(value, start, end)```**:检查字符串是否是以指定子字符串开头，如果是则返回 True，否则返回 False
2.  **```string.endswith(value, start, end)```**:判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回 True，否则返回 False

## dict

## tuple

## set