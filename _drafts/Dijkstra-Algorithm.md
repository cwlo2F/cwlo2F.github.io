---
layout: post
title: Dijkstra's Algorithm
tags:
  - Graph-Theory
  - Problem-Solving
mathjax: true
date: 2022-06-11 22:27:58
---



# 개요
유한 유향 그래프 $G = (V, A)$와 호 가중치 $w: A \to \mathbb{Z}_{\ge 0}$, 그래프의 두 꼭짓점 $s, t \in V$가 주어진다. 경로 또는 걸음에 대해 그 **가중치**는 그것을 구성하는 호의 가중치를 모두 합한 것이다. 다익스트라 알고리즘은 $s$에서 출발하여 $t$로 도착하는 경로 중 가장 가중치가 작은 것의 가중치를 시간복잡도 $\mathcal{O}(|V| + |A| \log |V|)$로 계산한다.


# 다익스트라 알고리즘

## 형식적 기술

우선 자료구조를 사용하지 않고 알고리즘을 기술하자. $S_0 = \emptyset$, $f_0: V \to \mathbb{Z}_{\ge 0} \cup \{\infty\}$, $$f_0(v) = \begin{cases} 0 & \mbox{if } v = s \\ \infty & \mbox{otherwise} \end{cases} $$를 정의한다. 편의를 위해 모든 꼭짓점 쌍 $u, v$에 대해 호 $(u, v)$가 존재하는 유향 그래프를 가정한다. 이때 존재하지 않는 호의 가중치는 $\infty$가 되고, 모든 $v \in V$에 대해 $w(v, v) = 0$이다. 가중치 함수는 $w: V \times V \to \mathbb{Z}_{\ge 0} \cup \{\infty\}$의 형태가 된다. $n = |V|$라고 하자. $i \in \mathbb{Z}_{> 0}$에 대해 $1 \le i \le n$번째 단계에 다음 절차를 수행한다.
1. $f_{i - 1}(u)$가 최소인 $u_i \in V \setminus S_{i - 1}$를 선택한다.
2. $S_i = S_{i - 1} \cup \{u_i\}$로 정의한다.
3. $v \in V$에 대해 $f_i(v) = \min\{f_{i - 1}(v), f_{i - 1}(u_i) + w(u_i, v) \}$로 정의한다.

**절차 $i.j$**는 $i$번째 단계에서 수행하는 $j$번째 절차이다. $f = f_n$라고 하자. $v \in V$에 대해 $f(v)$는 $u$에서 출발하여 $v$로 도착하는 경로 중 가중치가 가장 작은 것의 가중치이다.

## 정당성 증명

WIP; 형식적 뭐시기를 정리하는 중.


## 구현

[C++ 구현](https://github.com/cwlo2F/problem-solving/blob/main/notes/dijkstra.cpp)

벡터와 우선순위 큐를 사용한다. $n$을 그래프의 꼭짓점 개수라고 하자. 각 꼭짓점은 $0, 1, 2, \cdots n - 1$으로 이름이 붙는다. 다익스트라 알고리즘을 통해 0에서 출발하여 $k$로 도착하는 최소 가중치 경로를 계산할 것이다. `WeightedVertex`는 꼭짓점의 이름 `v`과 가중치 `w`를 함께 저장하는 구조이다. `WeightedVertex` `a, b` 사이의 비교 함수 `a < b`는 `a.w < b.w`로 정의된다. `graph[i]`의 원소 `x`는 그래프에서 가중치가 `x.w`인 호(`i`, `x.v`)를 나타낸다. `f`는 각 꼭짓점에 대해 0으로부터의 최단 경로의 가중치를 저장하기 위한 배열이다. 우선순위 큐 `pq`는 절차 1을 수행하기 위해 도입된다.