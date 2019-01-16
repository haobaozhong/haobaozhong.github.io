---
layout: post
title: "多点创造，少点劳苦"
date: 2018-12-10 18:00:00
categories: translation
---

# 多点创造，少点劳苦

作者：Betsy Beyer, Brendan Gleason, Dave O'Connor, Vivek Rau. Google SRE.

这篇文章基于 Vivek Rau 在《Site Reliability Engineering: How Google Runs Production Systems》中的“减少劳苦”章节。我们一开始重述了 Vivek 对于“劳苦”的定义，以及谷歌是怎样平衡运维和工程项目工作的。Bigtable SRE 的案例展示了一个真实的例子：一个谷歌团队怎样减少劳苦。最后，我们给了读者一系列最佳实践，对于减少劳苦有帮助，无论组织大小和构成。

## SRE’s Approach to Toil

正如在《SRE》一书中讨论的，谷歌 SRE 力图将工程师花费在运维工作上的时间控制在 50%。由于“运维工作”有多种解释方式，我们使用一个特殊的词来描述我们力图减少的工作：劳苦。

### “劳苦”的定义

为了定义劳苦，我们开始列举什么不是“劳苦”。“劳苦”不简单等同于：

- “我不喜欢的工作”
- 行政性工作。比如团队会议、设立和评估目标、人力资源文字性工作
- 蹩脚的工作。比如清理服务报警配置，以去除杂乱无用的报警
  “劳苦”是指这一类工作：
- 手工的
- 重复的
- 可以自动化、不需要人工干涉的
- 随时被打断的，响应式的
- 没有长期价值
  有长期价值的工作会使一项服务长期更好，然而“劳苦”是“快点搞定，原地不动”。劳苦随着服务的大小、流量或用户基数线性增长。因此，随着一项服务增长，没有被制止的劳苦会迅速占用所有人所有时间。

根据谷歌 SRE 报告，Top3 劳苦是（降序）：

1. 被打断（非紧急服务相关消息和邮件）
2. 随叫随到响应（紧急）
3. 发布和推送
   劳苦并不是永远都是坏的；所有 SRE（其他工程师）都需要处理一定量的劳苦。但是劳苦量很大时会变得有害，包括导致职业停滞和士气低落。花大量时间在劳苦工作上伤害了 SRE 组织，破坏了专注于工程的任务，减慢了开发速度，开了不好的先例，增加了摩擦，破坏了当初承诺给新员工的有趣的工程工作。

## 通过工程减少劳苦

SREs 承担的项目工作是把“劳苦”工作维持在可控水平的关键。将运维工作限制在 50%释放了其他的 SRE 时间用来做长期工程项目工作，这些工作的目的是减少劳苦和增加服务特性。这些新特性一般专注于提高可靠性、性能或实用功能——往往同时减少了劳苦。

### SRE 工程工作一般分为两类：

- **软件工程**。包括编写和修改代码，以及相关设计和文档工作。例如编写自动化脚本、创建工具或框架、增加扩展性和可靠性服务功能、修改基础架构代码使之更健壮。
- **系统工程**。包括配置生产系统，修改配置，编写长期有益的系统文档。例如监控设置和更新，负载均衡配置，服务器配置，操作系统参数调优，负载均衡设置等。系统工程还包括对开发团队提供架构、设计、上线咨询。
  工程性工作使 SRE 组织针对服务大小亚线性增长，与纯开发团队或者纯运维团队相比提供更高效的管理服务。

## 减少劳苦的最佳实践

现在我们看到了谷歌内一个 SRE 团队怎样处理劳苦，你可以从一个大规模运维中学到哪些应用于自己的公司和组织？
SRE 团队在谷歌的任务是维护谷歌线上各种服务，团队不同，减少劳苦的方式也不尽相同。虽然 Bigtable SRE 团队的一些特殊方式可能并不全部都适用，我们总结了 SRE 减少劳苦的方法为一些重要的最佳实践。不管你从头开始从事服务管理还是帮助一个被大量劳苦所困的团队，这些建议都适用。

### 管理层支持、采用很重要

正如 Bigtable SRE 案例研究中所得到的，你需要的到管理层帮助，需要管理层认同减少劳苦是一项有价值的目标。有时长期利益伴随着短期利益的牺牲和妥协，要让管理层支持暂停日常重要的工作说起来容易做起来难。重点是让管理层意识到这会使一个团队长期显著提高效率。例如，Bigtable SRE 团队只能短期内通过降低特性开发和耗时的客户请求的优先级来降低团队压力。
Bigtable SRE 发现把减少劳苦的方法分解为一系列小项目非常重要。这种增量的方式给团队一种靠近目标前进的动力。而且使管理者评估和纠正项目的方向。最后使进度很早可见，从外部利益相关者和领导者角度提高采用。

### 减少特殊需求

使用“宠物和牛群”比喻，你的系统需要自动化，容易互换，可替换，低维护成本（种群）；而不需要人类特殊照顾、特殊需求（宠物），如果你的系统很容易从头重建，灾难发生时，就会很好。手动迎合单个用户或客户的需求看起来很有吸引力，但是这样无法扩展。
同样的，理解出问题时两部分系统的不同，一部分需要人工关注和介入，一部分只需要自愈和自动替换。根据规模不同，这些部分可以是主机、机架、网络连接甚至整个集群。
慎重考虑配置管理。通过使用 Puppet 类似的中心控制工具，你得到系统的可扩展性、一致性、可靠性、可重复性、变更管理控制，使你按需分配新实例、推送变化。
虽然很多人和团队认识到构建一次性解决方案是次优的，但很容易构建类似系统。需要团队领导和管理者定期关注和检查，才能坚持标准化、同构的解决方案，而不是为了短期利益应付特殊情况。

### 尽早投资构建/测试/发布基础架构

标准化和自动化事件在服务早期可能很难推行，但是在整个过程中会多次受益。在后期实现这个架构会更加困难，不管技术上和还是组织上。

That said, there’s a balance between insisting on this approach wholesale, thus hurting velocity, versus postponing infrastructure development until suboptimally late in the development cycle. Try to plan accordingly—once you’re beyond the rapid launch­and­ iterate phase and relatively certain that the system will have the longevity to warrant this kind of investment, put sufficient time and effort into developing build, test, and release infrastructure.

### 经常性审计监控

树立一个经常回顾循环，去评估监控设置中的信号和噪声。要无情的深入溢出噪声和非行动性报警。否则，重要的你真正需要关注的报警会淹没在噪声中。对于每一个实时报警，重复思考，“一个人此刻必须做什么？”《SRE》一书中《监控分布式系统》这一章节有更深入探讨。

### 事后分析 Conduct Postmortems

事后分析可能并不出现在日常工作中，但是持续大量进行有益于系统或服务的稳定。在事故发生时，除了使系统恢复正常运行外，在危机解决后立即花时间去寻找真正原因。
The need for postmortems may not surface in the course of everyday work, but consistently undertaking them massively contributes to the stability of a system or service. Instead of just scrambling to get the system back up and running every time an incident occurs, take the time to identify and triage the root cause after the immediate crisis is resolved. As detailed in the SRE chapter “Postmortem Culture: Learning from Failure,” these collaborative postmortem documents should be both blameless and actionable. Avoid one­size­fits­all approaches: this exercise should be lightweight for small and simple inci­ dents but much more in­depth for large and complex outages.
No Haunted Graveyards
Even when it comes to companies and teams that consider themselves fast­moving and open to risk, parts of produc­
tion or the codebase are sometimes considered “too risky” to change—either very few people understand these components or they were designed in such a way that there’s a risk assigned to changing or touching them. Our goal is to control trouble, not to avoid it at all costs. In such cases of perceived risk, smoke out risk rather than leaving it to fester.

原文地址：[Invent More, Toil Less](https://ai.google/research/pubs/pub45765)
