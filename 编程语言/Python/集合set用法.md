# set是什么？用来干什么？

python中，用set来表示一个无序不重复元素的序列。set的只要作用就是给数据去重。

可以使用大括号 { } 或者 set() 函数创建集合，但是注意如果创建一个空集合必须用 set() 而不是 {}，因为{}是用来表示空字典类型的。

# set的集合的创建与使用

## 1.用{}创建set集合

```Python
person ={"student","teacher","babe",123,321,123} #可以赋值不同类型数据，也可以有重复数据，但是存储会去重
print(len(person))  #存放了6个数据，长度显示是5，存储是自动去重
print(person)       #打印出来是去重的

'''
5
{321, 'teacher', 'student', 'babe', 123}
'''
```

## 2.空set集合用set()函数表示

```Python
person1 = set()     #表示空set，不能用person1={}
print(len(person1))
print(person1)

'''
0
set()
'''
```

## 3.用set()函数创建set集合

```Python
person2 = set(("hello","jerry",133,11,133,"jerru")) #只能传入一个参数，可以是list,tuple
print(len(person2))
print(person2)

'''
5
{133, 'jerry', 11, 'jerru', 'hello'}
```

---

## 1.set对字符串也会去重，因为字符串属于序列。

```Python
str1 = set("abcdefgabcdefghi")
str2 = set("abcdefgabcdefgh")
print(str1,str2)
print(str1-str2)            #-号可以求差集
print(str2-str1)            #空值
#print(str1+str2)           #set里不能使用+号

{'d', 'i', 'e', 'f', 'a', 'g', 'b', 'h', 'c'} {'d', 'e', 'f', 'a', 'g', 'b', 'h', 'c'}
{'i'}
set()
```

## 2.set集合的增删改查操作

  ### 1.给set集合增加数据

  ```Python
  person ={"student","teacher","babe",123,321,123}
  person.add("student")   #如果元素已经存在，则不报错，也不会添加,不会将字符串拆分成多个元素，区别于update
  print(person)
  person.add((1,23,"hello")) #可以添加元组，但不能是list
  print(person)
  
  '''
  {321, 'babe', 'teacher', 'student', 123}
  {(1, 23, 'hello'), 321, 'babe', 'teacher', 'student', 123}
  '''
  ——————
  person.update((1,3)) #可以使用update添加一些元组列表，字典等。但不能是字符串，否则会拆分
  print(person)        #加进去的元组被拆分成了两个元素
  person.update("abc")
  print(person)  #会将字符串拆分成a,b，c三个元素
  
  '''
  {321, 1, 3, 'teacher', (1, 23, 'hello'), 'babe', 'student', 123}
  {321, 1, 3, 'b', 'c', 'teacher', (1, 23, 'hello'), 'a', 'babe', 'student', 123}
  '''
  ```

  ### 2.从set里删除数据

  ```Python
  person.remove("student")    #按元素去删除
  print(person)
  #print("student")           如果不存在 ，会报错
  
  '''
  {321, 1, 3, 'c', 'b', (1, 23, 'hello'), 'teacher', 'babe', 'a', 123}
  '''
  ——————
  person.discard("student")   #功能和remove一样，好处是没有的话，不会报错
  person.pop()                #在list里默认删除最后一个，在set里随机删除一个。
  print(person)
  
  '''
  {1, 3, (1, 23, 'hello'), 'teacher', 'b', 'a', 'babe', 123, 'c'}
  '''
  ```

  ### 3.更新set中某个元素

  因为是无序的，所以不能用角标，一般更新都是使用remove,然后再add

  ### 4.查询是否存在，无法返回索引，使用in判断

  ```Python
  if "teacher" in person:
      print("true")
  else:
      print("不存在")
      
  '''
  true
  '''
  ```

  ### 5.终极大招：直接清空set

  ```Python
  print(person)
  person.clear()
  print(person)
  
  '''
  set()
  '''
  ```

## 3.求交集、并集、差集

好处是避免采用遍历的方法即可求出结果，大幅提高运算速度

```Python
A={1,3,5,9,6}
B={1,3,5,2,0}

list(A.intersection(B))         #A∩B
Out[1]: [1, 3, 5]

list(A.union(B))                #A∪B
Out[2]: [0, 1, 2, 3, 5, 6, 9]

list(A.difference(B))           #在A中但不在B中
Out[3]: [9, 6]
```

