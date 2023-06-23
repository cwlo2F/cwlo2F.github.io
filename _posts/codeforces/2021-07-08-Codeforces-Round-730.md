---
layout: post
title: Codeforces Round 730
tags:
  - Problem-Solving
  - Codeforces
categories: Codeforces
mathjax: true
date: 2021-07-08 04:30:00
---

# 콘테스트 기록

A, B는 어렵지 않게 풀었다. C는 실수가 나와서 당황했는데, 어쨌든 오차가 아주 중요한 문제는 아니었다. D는 interactive형 문제였는데, 처음 보는 형태라서 조금 얼탔다. E는 튜토리얼을 읽고 업솔빙 중이다. A는 00:05에, B는 00:11에, C는 00:39에, D1은 01:05에, D2는 01:38에 풀었다. E는 풀지 못했다. 

최종적으로 58위가 되었고, 아주 좋은 결과라고 생각한다.

# 1543A Exciting Bets

$b - a$는 불변량이다. $a = b$이면 $a, b$를 증가시킬 때 흥분<sup>excitement</sup>도 항상 증가하고, 팬들은 무한한 흥분을 얻는다. $d = |b - a| > 0$일 때, $a, b$를 조작하여 모두 $d$의 배수가 되도록 하였을 때 $\gcd(a, b) = d$이다. $d$보다 큰 수 $d'$에 대해 $a, b$를 $d'$로 나눈 나머지가 다르므로 이는 $a, b$의 최대공약수가 될 수 없다. 따라서 흥분의 최댓값은 $d$가 된다. $a, b$가 $d$의 배수에 이르기까지 조작이 덜 필요한 쪽을 선택하여 증가시키거나 감소시키면 된다.

# 1543B Customising the Track

$a_i$가 오름차순으로 정렬되어 있다고 가정하자. $a_n - a_1 \ge 2$인 경우, $a_1, a_n$을 각각 $a_1 + 1, a_n - 1$으로 바꾸었다고 하자. $a_i = a_1$을 만족하는 $i$의 최댓값을 $p$, $a_j = a_n$을 만족하는 $i$의 최솟값을 $q$라고 하자. $a_n - a_1 > 0$이므로 $p < q$이다. 값을 변경하였을 때 불편<sup>inconvenience</sup>의 변화량을 다음과 같이 계산할 수 있다.

$$ \sum_{j = 2}^{n - 1} |a_1 + 1 - a_j| = p - 1 + \sum_{j = p + 1}^{n - 1} |a_1 - a_j| - n + p + 1 $$
$$ \sum_{j = 2}^{n - 1} |a_j - a_n + 1| = n - q - 1 + \sum_{j = 2}^{q - 1} |a_j - a_n| - q + 2 $$
$$|a_1 + 1 - a_n + 1| = |a_1 - a_n| - 2$$
$a_1 \leftarrow a_1 + 1$, $a_n \leftarrow a_n - 1$으로 변경했을 때 불편의 변화량은 $2p - 2q - 1 < 0$이 된다. 배열을 다시 정렬했을 때 $a_n - a_1 \ge 2$인 한, 불편을 계속하여 감소시킬 수 있다. 따라서 $a_n - a_1 \ge 2$가 되는 분배는 최적해가 아니다.

$a_n - a_1 \le 1$라고 가정하면, 이를 만족하는 분배는 $k, \cdots, k, k + 1, \cdots, k + 1$의 형태이다. $k$와 $k + 1$의 개수가 각각 $l, m$일 때 원하는 답은 $l \cdot m$이다. $S = \sum_{i = 1}^n a_i$일 때, $m = S \mod n$, $l = n - m$이다.

# 1543C Need for Pink Slips

기댓값의 의미를 잘 생각하고, 문제에서 주어진 설명을 잘 따라서 재귀 함수를 잘 구성하여 완전 탐색으로 풀 수 있다... 실수 오차나 스택 오버플로우 등을 상상하면 두려워지는데, Pink Slip를 뽑지 않을 때마다 Pink Slip을 뽑을 확률이 적어도 0.05 증가하므로 많아야 20단계 내에 끝나게 된다.

# 1543D RPD and Rap Sheet

비밀번호를 $y$로 추측할 때마다, 틀린 추측이라면 원래 비밀번호 $x$는 $x \oplus_k z = y$를 만족하는 $z$로 바뀐다. $x$를 $m$번 $k$-itwise XOR한 것을 $(\oplus m) \cdot x$로 표기하자. 즉, $(\oplus m) \cdot x = x \oplus_k \cdots \oplus_k x$인데 우변의 식에서 $x$는 $m$번 등장한다. $(\oplus m) \cdot ((\oplus n) \cdot x) = (\oplus mn) x$를 관찰하자. 

양 변에 $- \oplus_k x$를 $k - 1$번 취하여 
$$z \oplus_k (x \oplus_k (\oplus k - 1) \cdot x) = z = y \oplus_k (\oplus k - 1) \cdot x $$
를 얻는다. 

$i = 0$번째 추측을 $y = 0$으로 하자. $i \ge 1$에 대해, $i$번째 추측을 $(\oplus (k - 1)^i) i \oplus_k (\oplus (k - 1)^{i - 1}) \cdot (i - 1)$으로 하자. 원래 비밀번호를 $x$라고 하자. $i \in \mathbb{Z}_{\ge 1}$번째 추측에 비밀번호를 틀렸을 때, 바뀐 비밀번호가 $(\oplus (k - 1)^i) \cdot i \oplus_k (\oplus (k - 1)^{i + 1}) \cdot x$라고 가정하자. 만약 $x = i + 1$이면, $i + 1$번째 추측에서 비밀번호를 맞추게 된다. $x > i + 1$이면 다음 비밀번호는
$$ \left( (\oplus (k - 1)^i) i \oplus_k (\oplus (k - 1)^{i - 1}) \cdot (i - 1) \right) \oplus_k (\oplus k - 1) \cdot \left( (\oplus (k - 1)^i) (i - 1) \oplus_k (\oplus(k - 1)^{i + 1}) \cdot x \right)  $$
이고, 이를 정리하면 $(\oplus (k - 1)^{i + 1}) \cdot (i + 1) \oplus_k (\oplus (k - 1)^{i + 2}) \cdot x$이 된다. 원래 비밀번호는 $[0, n)$에 있으므로, 귀납법을 통해 $i = 0, \cdots, n - 1$에 대해 $i$번째 추측을 시도하였을 때 이 중 한 번은 옳은 추측임을 알 수 있다. 

임의의 $m$에 대해 $(\oplus k - 1) \cdot ((\oplus k - 1) \cdot m) = (\oplus (k-1)^2) m = m$이므로, 이를 이용하여 $i$번째 추측 $(\oplus (k - 1)^i) i \oplus_k (\oplus (k - 1)^{i - 1}) \cdot (i - 1)$를 계산해서 1을 입력받을 때까지 출력하면 된다.