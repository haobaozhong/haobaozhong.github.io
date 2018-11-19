---
layout: post
title: "面向对象编程之害"
date: 2018-11-19 10:00:00
categories: programming
---

## 继承

### 问题

> The problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle. - **Joe ArmStrong**
>
> 面向对象编程语言的问题在于他们携带隐含的环境。你想要一个香蕉，但是得到了一个拿着香蕉的大猩猩，还有整个丛林。

- **脆弱性**。继承体系设计和实现不当时，会导致非常脆弱的结构，维护性变差。比如基类变化时，即便你的代码没有变化，也可能导致错误。
- **多重继承**。不能很好支持多重继承，多重继承有害，却存在现实世界中。

### 解决方案

- **组合**。组合优于继承。
- **代理**。行为代理，比如 JavaScrit 中的原型。

## 封装

### 问题

- **引用**。对象引用并没有得到封装，处处深拷贝不大可行。

## 多态

### 问题

- **接口**。基于接口的多态更好。

## 解决方案

- **一切皆权衡**。
- **Everything is a trade-off**.
- 函数式编程
- 组合
- 接口
- 多范式编程语言：Go

## 资源

- [Goodbye, Object Oriented Programming](https://medium.com/@cscalfani/goodbye-object-oriented-programming-a59cda4c0e53)
