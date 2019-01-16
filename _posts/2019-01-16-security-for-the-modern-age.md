---
layout: post
title: "现代应用安全"
date: 2019-01-16 10:00:00
categories: security
---

当在云上面部署应用时，实践者寻求当前任务最具有操作性的工具集合，决定“正确”的工具很重要。回到 2013 年，Docker 由于其易用性赢得了开发者青睐，但是 Linux 容器本身从 2007 年就存在，当时`cgroups[control groups]`加入了内核。当前，容器催生了一个开发者每天使用的新工具和实践的生态。构成容器的基础技术并不是全新的。不像 Solaris Zones 和 FreeBSD Jails，Linux 容器不是把隔离性放在首位的内核组件，而是内核的一组技术，比如：namespaces，cgroups，AppArmor，SELinux(Security-Enhanced Linux)。
容器并不是开发者遇到的典型抽象，当前的趋势是函数和`Serverless`，使得用户可以在云上运行函数。由于应用和函数在云上运行，可能会有一个新的以边界安全的方式运行单个线程的隔离技术。

虽然有证明一个良好设计的运行在安全模式的容器和虚拟机管理程序提供了大致相同的安全性，仍然需要安全的方法来运行需要整个系统调用接口的线程。解决这个问题带来了一些有意义的研究。

## 虚拟机和容器

## 应用安全的未来

容器生态节奏很快，很多公司都在基于现有技术构建产品，同时用这些技术和产品运行自己的基础架构。这三篇论文的焦点在于现代应用安全的进展。

# 作者

- 译自 ACM Queue[Security for the Modern Age](https://queue.acm.org/detail.cfm?id=3301253)
- 作者 Jessie Frazelle
- Volume 16, issue 5
