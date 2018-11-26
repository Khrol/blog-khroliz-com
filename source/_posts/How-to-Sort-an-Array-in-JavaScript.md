---
title: How to Sort an Array in JavaScript?
date: 2018-11-26 10:11:28
tags: JavaScript
---

During the preparation to one of the interviews, I've decided to try solving [HackerRank](https://hackerrank.com) tasks in JavaScript instead of Python.
I've chosen a relatively [simple task](https://www.hackerrank.com/challenges/fraudulent-activity-notifications/problem) and started to write the code.

I had to sort an array and everything seemed to work well.

```JavaScript
> Array(5, 8, 7, 2).sort()
[ 2, 5, 7, 8 ]
```

But when I've submitted a solution I got `Wrong Answer` result.

After 10 minutes of debugging the following behavior was discovered.

```JavaScript
> Array(5, 8, 7, 2, 22).sort()
[ 2, 22, 5, 7, 8 ]
```

Nice! JavaScript is sorting numbers as strings by default.
If you want to sort numbers in JavaScript, you should bypass custom predicate to the sorting function. 

```JavaScript
> Array(5, 8, 7, 2, 22).sort((a, b) => a - b)
[ 2, 5, 7, 8, 22 ]
```

Such behavior looks reasonable for front-end. But JavaScript is used on the back-end as well and this seems like very dangerous default sorting. All your tests will be green until you put some double-digit numbers.
