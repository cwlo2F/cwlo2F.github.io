---
layout: post
title: Codeforces Round 729
tags:
  - Problem-Solving
  - Codeforces
categories: Codeforces
mathjax: true
date: 2021-07-04 02:00:00
updated: 2021-07-04 23:59:59
---

# 콘테스트 기록

A, C는 많이 어렵지 않게 풀었다. B 풀이가 상상이 안되어서, B에 많은 시간을 사용했다. D는 B를 푼 이후 문제를 읽고 문제 풀이 전략을 구상하였는데, 아이디어만 남긴 채 다 풀지는 못 하였다. E1, E2는 문제를 읽지 않았다. A는 00:02에, C는 00:39에, B는 01:21에 풀었다. D는 콘테스트 종료 후에 풀었다. E1, E2는 풀지 못했다.

# 1542A Odd Set

두 수의 합이 홀수가 되기 위해서는 홀수와 짝수가 짝지어져야 하므로 홀수와 짝수의 개수가 각각 $n$과 같은지 확인하면 된다.

# 1542B Plus and Multiply

문제에서 주어진 집합을 $S$라고 하자. $S = T_{a, b} := \{a^m + b \cdot k: m, k \in \mathbb{Z}_{\ge 0}\}$이다. 다음을 관찰하자.
1. $1 = a^0 + b \cdot 0 \in T_{a, b}$이다.
2. $a^m + b \cdot k \in T_{a, b}$에 대해, 
$$(a^m + b \cdot k) \cdot a = a^{m + 1} + b \cdot ak \in T_{a, b},$$ 
$$a^m + b \cdot k + b = a^m + b \cdot (k + 1) \in T_{a, b}$$
이다.

따라서 $S \subset T_{a, b}$이다. 한편 모든 $a^m + b \cdot k$꼴의 수는 항상 $1 \cdot a \cdot \cdots \cdot a + b + \cdots + b$와 같이 표현되므로 $S$의 원소이고 $T_{a, b} \subset S$이다.

$m$을 늘려가며 $n - a^m$이 음이 아닌 $b$의 배수가 되는 $m$이 존재하는지 확인하여 $n \in T_{a, b} = S$인지 판정할 수 있다.

# 1542C Strange Function

$m(k)$을 $1, 2, \cdots, k$의 최소공배수라고 하자. $f(x) = k$은 $x$가 $m(k - 1)$의 배수이면서 $m(k)$의 배수가 아닌 것과 동치이다. $m(0) = 1$으로 정의하자. $[n]$에서 $m(k)$의 배수의 개수는 $\left\lfloor \frac{n}{m(k)} \right\rfloor$이므로, 구하려는 답은 
$$\sum_{k = 1}^\infty k \cdot \left( \left\lfloor \frac{n}{m(k - 1)} \right\rfloor - \left\lfloor \frac{n}{m(k)} \right\rfloor \right) = \sum_{m(k) \le n} k \cdot \left( \left\lfloor \frac{n}{m(k - 1)} \right\rfloor - \left\lfloor \frac{n}{m(k)} \right\rfloor \right) $$
이다. 이때 $m(k) > n$이면 $\left\lfloor \frac{n}{m(k)} \right\rfloor = 0$이다. 이를 만족하는 가장 작은 $k$를 $k_0$라고 하자. 식을 다시 써 보면 
$$ \left\lfloor \frac{n}{m(0)} \right\rfloor + \sum_{k = 1}^{k_0} ((k + 1) - k) \left\lfloor \frac{n}{m(k)} \right\rfloor = n + \sum_{k = 1}^{k_0} \left\lfloor \frac{n}{m(k)} \right\rfloor$$
이고, 이는 쉽게 계산 가능하다.

# 1542D Priority Queue

각 `+ x` 기호에 대해 이 $x$가 답에 어떻게 기여하는지 상상하는 것이 하나의 풀이 전략이 될 수 있다. 각 $x$에 대해, 배열 $Q_x$를 할당한다. 이는 우선순위 큐 $T$에 현재 $x$보다 먼저 나가는 원소의 개수를, 그러한 상황을 만드는 $A$의 부분 문자열의 개수에 대응시킨다. 같은 값에 대해서는 나중에 들어온 것이 먼저 나간다고 가정할 수 있다. 주어진 명령들을 순서대로 순회하면서 `+ x` 이전의 명령들과 `+ x` 이후의 명령들에 대해 $Q_x$에 적절한 연산들을 취하여 $Q_x$가 그 목적에 맞도록 바꿀 수 있다. $Q_x$에 남아있는 항을 모두 더하고 이를 $x$와 곱하여 답을 저장할 변수에 더한다. 이를 모든 `+ x` 명령에 대해 반복하여 답을 얻을 수 있다. $Q_x$의 크기를 $n$으로 잡으면, 이 방법의 시간 복잡도는 $\mathcal{O}(n^3)$이 된다. $n \le 500$이므로 충분히 사용할 수 있는 풀이이다.