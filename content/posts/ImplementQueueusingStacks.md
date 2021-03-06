---
title: "LeetCode-232-用栈实现队列"
date: 2019-05-21T11:06:17+08:00
draft: false
tags: ["算法","Leetcode"]
categories: ["Algorithm"]
---

# Implement Queue using Stacks
**Leetcode 232.Implement Queue using Stacks**

Implement the following operations of a queue using stacks.
* push(x) — Push element x to the back of queue.
* pop() — Removes the element from in front of queue.
* peek() — Get the front element.
* empty() — Return whether the queue is empty.

**Example:**
```python 
MyQueue queue = new MyQueue();

queue.push(1);
queue.push(2);  
queue.peek();  // returns 1
queue.pop();   // returns 1
queue.empty(); // returns false
```

```python
# @Author：Kilien
# @lc app=leetcode id=232 lang=python3
# [232] Implement Queue using Stacks
# time:O(1) space:O(n)
#思路：两个数组，模拟入栈出栈，实现队列；具体见图解
class MyQueue:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.inStack, self.outStack = [], []

    def push(self, x):
        """
        :type x: int
        :rtype: nothing
        """
        self.inStack.append(x)

    def pop(self):
        """
        :rtype: nothing
        """
        self.move()
        return self.outStack.pop()

    def peek(self):
        """
        :rtype: int
        """
        self.move()
        return self.outStack[-1]

    def empty(self):
        """
        :rtype: bool
        """
        return (not self.inStack) and (not self.outStack) 
        
    def move(self):
        """
        :rtype nothing
        """
        if not self.outStack:
            while self.inStack:
                self.outStack.append(self.inStack.pop())

# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()

```

初始建两个数组模拟栈：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack1.png" title="stack1" >}}

字符串”1，2，3“入栈：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack2.png" title="stack2" >}}

”1，2，3“移动至outStack：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack3.png" title="stack3" >}}

”4，5“入栈，”1，2，3“依次出栈，输出字符串”1，2，3“：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack4.png" title="stack4" >}}

”4，5“移动至outStack：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack5.png" title="stack5" >}}

输出”4，5“：
{{< figure src="https://cdn.jsdelivr.net/gh/KiLien/Pics/Algm/LC_232_stack6.png" title="stack6" >}}
