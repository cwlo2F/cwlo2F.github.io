---
title: Educational Codeforces Round 129
tags:
  - Problem-Solving
  - Codeforces
categories: Codeforces
mathjax: true
date: 2022-05-24 03:00:00
update: 2022-05-24 03:00:00
---




# 콘테스트 기록
A, B, C, D를 어렵지 않게 풀었다. E는 좀 더 집중을 했으면 풀었을지도 모르지만 아직 풀지 않았다. F는 읽고 문제 내용을 이해했지만 해결법을 전혀 모른다.

|A|B|C|D|E|F|
|:---:|:---:|:---:|:---:|:---:|:---:|
|00:07|00:12|00:25|00:47|-|-|




# 1681A Game with Cards

각 경기자의 최선의 수는 자신이 가지고 있는 가장 큰 수 카드를 내는 것이다. Alice를 선공, Bob을 후공이라고 하자. Alice와 Bob이 가진 카드에 적힌 수 중 가장 큰 것을 각각 $A, B$라고 하자. 

* $A \ge B$이면, Alice가 첫 수로 $A$를 냈을 때 Bob이 대응할 수 있는 수가 없다.
* $A < B$이면, 두 번째 수로 Bob은 항상 $B$를 낼 수 있고, Alice는 이에 대응할 수 있는 수가 없다.

Bob이 선공인 경우에도 마찬가지 분석을 할 수 있다.


# 1681B Card Trick

법 $n$에 대해 $1 + \sum_{j = 1}^m b_j$번째 카드를 찾으면 된다.

# 1681C Double Sort

수학적 귀납법을 통해 풀이와 정당성을 얻을 수 있다. $1 \le i \le n$에 대해 $1, 2, \cdots, i - 1$번째 원소가 정렬되었다고 하면, 정렬되지 않은 원소 중 $a_j, b_j$가 동시에 최솟값이 되는 $j$를 $i$번째 자리에 넣으면 $1, 2, \cdots, i$번째 원소가 정렬된다. 이러한 $j$를 찾을 수 없으면, 주어진 $a, b$는 원하는 상태에 도달할 수 없다.

# 1681D Required Length

`long long`을 사용할 수 있는데, 표시할 수 있는 최댓값이 $9 \cdot 10^{18}$보다 크고, 연산은 항상 $10^{18}$보다 작은 수와 9 이하의 수의 곱을 통해 새로운 수를 만들기 때문이다. 새로 만들어지는 수는 주어진 $x$에 대해 항상 $2^{e_2} \cdot 3^{e_3} \cdot 5^{e_5} \cdot 7^{e_7} \cdot x$꼴이고, 위에서 관찰했듯 이러한 수는 $2^{63}$이하이다. $e_2 + e_3 + e_5 + e_7 \le 63$을 얻을 수 있는데, 이를 만족하는 $(e_2, e_3, e_5, e_7)$은 많아야 ${63 + 4 \choose 4} = 766480$가지로, 수가 많지 않다. 따라서 단순히 BFS로 해결할 수 있다. 