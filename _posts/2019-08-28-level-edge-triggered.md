---
layout: post
title: "Level-triggered vs Edge-triggered Programming"
date: 2019-08-28 10:00:00
categories: design
---

### Level-triggered vs Edge-triggered Programming

![level-vs-edge-triggered](/assets/img/level-edge-triggered.svg)

| level-triggered | edge-triggered |
| --------------- | -------------- |
| state           | event          |

### edge-triggered programming
#### examples
- producer/consumer
- publisher/subscriber
- observer
- event

#### take away
- work well in a single process
- tends not to work so well in distributed systems, due to [Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
- when bad things inevitably happen,you drop back to a level-triggered mechanism that reconcile discrepancies in state
- it's ok to use, but think in it

### References

- [Level-triggered and edge-triggered](http://gengnosis.blogspot.com/2007/01/level-triggered-and-edge-triggered.html)
- [Level Triggering and Reconciliation in Kubernetes](https://hackernoon.com/level-triggering-and-reconciliation-in-kubernetes-1f17fe30333d)
- [wiki: Flip-flop (electronics)](https://en.wikipedia.org/wiki/Flip-flop_(electronics))
