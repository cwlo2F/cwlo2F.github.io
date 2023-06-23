---
title: Educational Codeforces Round 111
tags:
  - Problem-Solving
  - Codeforces
categories: Codeforces
mathjax: true
date: 2021-07-22 03:14:03
---


# 콘테스트 기록

A, B를 어렵지 않게 풀었고 C는 아이디어를 생각해내는데 시간을 좀 썼다. D, E, F는 무진장 어려웠다. A는 00:04, B는 00:11, C는 00:35에 풀었다. D, E, F는 풀지 못했다.

# 1550A Find The Array

길이 $n$인 수열로 최대 $n^2$까지 만들 수 있다. 길이 $m$인 수열의 합이 $l$일 때, 가장 큰 항의 값을 1 줄임으로써 길이 $m$이고 합이 $l - 1$인 수열을 만들 수 있다. $\left\lfloor \sqrt{n - 1} \right\rfloor + 1$가 원하는 답이 된다.

# 1550B Maximum Cost Deletion

연속하는 문자열을 지운 횟수를 $k$라고 할 때, 전체 점수는 $an + bk$이다. 연속하는 조각의 개수가 $m$일 때, 이는 최소 $m / 2 + 1$번 지워야 하고, 최대 $n$번까지 지울 수 있다. $an + \max\{b \cdot (m/2 + 1), bn\}$이 원하는 답이 된다.

# 1550C Manhattan Subarrays

$d(p_i, p_k) = d(p_i, p_j) + d(p_j, p_k)$인 경우, $j$는 $i$와 $k$ 사이에 있다. $i < k$를 가정하면, $i < j < k$이다. 또한 $a_j$는 $a_i, a_k$ 사이에 있고, $a_i, a_j, a_k$는 단조증가 혹은 단조감소이다.

Erdős-Szekeres 정리에 의해 길이가 5인 수열은 항상 길이 3인 단조증가하는 부분수열 또는 길이 3인 단조감소하는 부분수열을 포함하고, 따라서 이는 항상 나쁜 수열이다. 각 $l = 1, \cdots, n$에 대해 $a_l, a_{l + 1}, a_{l + 2}, a_{l + 3}$의 좋은 부분 수열의 개수를 찾아서 더하면 원하는 답이 된다.
