---
title: Java 反射学习记录
date: 2022-08-29 14:47:03
tags: Java
---
### 反射

- 对于任何一个class类，在运行时可以直接得到这个类的全部成分
- 在运行时可以直接得到这个累的构造器对象：Constructor
- 可以直接得到成员变量field
- 得到成员方法对象Method
- 可以运行时动态获取类的信息以及动态调用类的成分称为Java语言的反射机制

1. #### 利用反射技术获取构造器对象的方式

    - getDeclaredConstructors()
    - getDeclaredConstructor(Class<?> .... parameterTypes)

2. #### 反射得到的构造器可以做什么

    - 依然是创建对象
        - public newInstance(Object...initars)
    - 如果是非public的构造器，需要打开权限（暴力反射），然后再创建对象
        - setAccessible(boolean)
        - 反射破坏封装性，私有的也可以执行了

3. #### 利用反射获取成员变量的方式

    1. 获取成员变量对象得方法
        - getDeclareFields()
        - getDeclareField(String name)

4. #### 反射得到的成员变量可以做什么

    1. 依然是在某一个对象中取值和赋值
        - void set(Object obj,Object value):
        - Object get(Object obj)
    2. 如果某个成员变量是非public的,需要打开权限（暴力反射），然后取值、赋值、
        - setAccessible(boolean)

5. #### 利用反射获取成员对象的方式

    1. 获取类中成员方法对象
        - getDeclareMethods()
        - getDeclareMethod(String name, Class<?>...parameterTypes)
    2. 可以做什么
        1. 依然是在对像中触发该方法执行
            - Object invoke(Object obj, Object...args)
        2. 如果某个成员方法是非public的,需要打开权限（暴力反射）
            - setAccessible(boolean)