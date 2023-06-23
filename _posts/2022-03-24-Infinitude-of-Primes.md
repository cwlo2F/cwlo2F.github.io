---
layout: post
title: Infinitude of Primes
tags: Number-Theory
mathjax: true
date: 2022-03-24 00:27:01
---


# 서문

**소수**는 그 양의 약수가 1과 자기 자신 이외에 존재하지 않고 1보다 큰 양의 정수이다. 예컨대, 7의 양의 약수는 1과 7이고 그 밖에 양의 약수는 존재하지 않으므로 7은 소수이다. 한편, 3은 57 = 3·19 의 양의 약수이다. 57은 소수가 아니다. 1보다 크고 소수가 아닌 양의 정수를 **합성수**라고 부른다. 57은 합성수이다.

소수는 무한히 많이 존재한다. 이 사실을 **소수의 무한성**<sup>**infinitude of primes**</sup>이라고 부른다. 이 글은 소수의 무한성의 여러가지 증명에 대해 소개한다.

## 유클리드<sup>Euclid</sup>의 증명

결론을 부정하여 소수의 무한성이 거짓이라고 가정하자. $\Pi$를 모든 소수로 이루어진 $\mathbb{Z}$의 부분집합이라고 하자. 모든 소수의 곱에 1을 더한 수
$$P = 1 + \prod_{p \in \Pi} p$$
를 생각하자. $\Pi$는 유한집합이므로 $P$는 잘 정의된다. 모든 $p \in \Pi$에 대해 
$$p \le \prod_{p \in \Pi} p < 1 + \prod_{p \in \Pi} p = P$$
이므로, $P$는 $\Pi$에 포함되지 않는다. $q$를 $P$의 소수인 양의 약수라고 하자. $P$는 모든 $\Pi$의 원소 $p$에 대해, $P$를 $p$로 나누었을 때 나머지가 1이 남고, 1은 $p$의 배수가 아니므로 $p$는 $P$의 약수가 아니다. 따라서 $q \not\in \Pi$인데, 이는 보조정리에 의해 $q$가 소수가 되어야 한다는 점과 모순이다. 따라서 소수의 무한성은 참이다.

## 에르되시<sup>Erdős</sup>의 증명

수열 $\{p_n\}$에는 모든 소수가 정확히 한 번씩 등장하고, 임의의 $i < j$에 대해 $p_i < p_j$를 만족한다고 하자. 만약 소수의 무한성이 거짓이어서 소수가 정확히 $N \in \mathbb{Z}_{\ge 0}$개 존재할 경우, 모든 $i \in \mathbb{Z}_{\ge 1}$에 대해 $p_{N + i} = +\infty$로 정의하자. $\frac{1}{+\infty} = 0$으로 정의하자.

**모든 소수 역수의 합** 무한합 $\displaystyle\sum_{n = 1}^\infty \frac{1}{p_n}$는 발산한다.

**증명** 결론을 부정하여 $\displaystyle\sum_{n = 1}^\infty \frac{1}{p_n}$이 실수 $L$에 수렴한다고 가정하자. $\displaystyle\sum_{n = k + 1}^\infty \frac{1}{p_n} < \frac{1}{2}$를 만족하는 가장 작은 정수 $k$를 선택하자. $p_1 = 2$이므로 $k \ge 1$, 특히 $k \neq 0$임을 관찰하자. 또한 조건에서 $k$의 최소성에 의해 $k$번째 소수 $p_k$는 존재하고, 특히 $p_k \neq +\infty$임을 관찰하자. 양의 정수 $N$에 대해, $N$보다 작거나 같은 양의 정수 중 그 소인수분해 $e: \Pi \to \mathbb{Z}_{\ge 0}$가
$$ e = e_k + 2e', $$
$$ \forall i \in [k].e_k(p_i) \in \{0, 1\}, $$
$$ \forall p \in \Pi.e'(p) \in \mathbb{Z}_{\ge 0} $$
와 같이 나타나는 것들의 개수와 관련된 부등식을 세우고 이에서 모순을 이끌어낼 것이다. 소인수분해가 위 조건과 같이 나타나는 $[N]$의 원소를 *좋은 수*라고 하자. $[N]$의 원소 중 좋은 수가 아닌 것을 *나쁜 수*라고 하자. 

* $[N]$의 원소 중 좋은 수의 개수는 많아야 $2^k \sqrt{N}$이다. $e_k$를 선택하는 경우의 수는 $2^k$이다. 소인수분해로 $e_k, e'$를 갖는 수를 각각 $r, s$라고 할 때, $s^2 \le \frac{N}{r} \le N$을 만족하므로 각 $e_k$에 대해 좋은 수는 많아야 $\sqrt{N}$개 존재한다. 
* $[N]$의 원소 중 나쁜 수의 개수는 많아야 $\frac{1}{2} N$이다. $m > k$에 대해, $[N]$의 원소 중 $p_m$의 배수는 $\left\lfloor \frac{N}{p_m} \right\rfloor$개 존재한다. 어떤 정수가 나쁜 수라는 것은 어떤 $m > k$에 대해 $e(p_m)$이 홀수인 것과 동치이고, 이때 그 수는 $p_m$의 배수가 된다. 따라서 나쁜 수들의 부분집합은 $m > k$에 대해 $p_m$의 배수의 부분집합의 합집합에 속하게 된다. 합집합 상한을 사용하면 나쁜 수의 개수에 대한 상한 
$$\sum_{n = k + 1}^\infty \left\lfloor \frac{N}{p_n} \right\rfloor \le \sum_{n = k + 1}^\infty \frac{N}{p_n} \le \frac{1}{2} N $$
을 얻는다.

좋은 수의 부분집합과 나쁜 수의 부분집합의 합집합은 $[N]$이므로, 부등식
$$N \le 2^k \sqrt{N} + \frac{1}{2} N$$
을 얻는다. 이를 정리하면 $N \le 4^{k + 1}$인데, 이는 명백히 어떤 양의 정수에 대해 성립하지 않는 부등식이다. $N = 4^{k + 1} + 1$을 선택하여 위 논증을 반복하면 모순을 얻게 되므로, 무한합 $\displaystyle \sum_{n = 1}^\infty \frac{1}{p_n}$가 수렴한다는 가정은 잘못되었다. 따라서 무한합 $\displaystyle \sum_{n = 1}^\infty \frac{1}{p_n}$은 발산한다.

## 퍼스턴버그<sup>Furstenberg</sup>의 증명

위상수학을 사용한 이 증명은 수학자 퍼스턴버그가 학부생 때 떠올렸다고 전해진다.

집합 $X$에 대해 $X$의 부분집합을 원소로 갖는 집합 $\mathcal{T}$가 다음 조건을 만족할 때, $\mathcal{T}$을 $X$의 위상이라고 한다.
1. $\emptyset \in \mathcal{T}, X \in \mathcal{T}$
2. 임의의 집합 $I$에 대해, $\forall i \in I.U_i \in \mathcal{T}$이면 $\bigcup_{i \in I} U_i \in \mathcal{T}$이다.
3. 임의의 양의 정수 $n$에 대해, $\forall i \in \{1, 2, \cdots, n\}.U_i \in \mathcal{T}$이면 $\bigcap_{i = 1}^n U_i \in \mathcal{T}$이다.

$U \in \mathcal{T}$인 $X$의 부분집합 $U$을 열린집합이라고 한다. $X \setminus U \in \mathcal{T}$인 $X$의 부분집합 $U$를 닫힌집합이라고 한다.

$a, b \in \mathbb{Z}$, $b \neq 0$에 대해 $U_{a, b} = \{a + bn: n \in \mathbb{Z}\}$으로 정의한다. 임의의 첨수 집합 $J$과 $a_j, b_j \in \mathbb{Z}$, $b_j \neq 0$에 대해 $U = \bigcup_{j \in J} U_{a_j, b_j}$으로 표현가능한 $U$를 원소로 갖는 $\mathbb{Z}$의 부분집합들의 집합 $\mathcal{T}$을 정의할 수 있다.

$\mathcal{T}$가 위상임을 보이자. 
1. $J = \emptyset$일 때 $\emptyset$는 빈 합집합이므로 $\emptyset \in \mathcal{T}$이다. $J = \{ \* \}$, $a_\* = 0$, $b_\* = 1$일 때 $\mathbb{Z} = U_{0, 1} = \bigcup_{j \in J} U_{a_j, b_j}$으로 $\mathbb{Z} \in \mathcal{T}$이다.
2. $i \in I$에 대해 $U_i = \bigcup_{j \in J_i} U_{a_{i, j}, b_{i, j}} \in \mathcal{T}$라고 하자. $K = \{(i, j): i \in I, j \in J_i\}$일 때 $K$는 집합이고 $\bigcup_{i \in I} U_i = \bigcup_{i \in I} \bigcup_{j \in J} U_{a_{i, j}, b_{i, j}} = \bigcup_{(i, j) \in K} U_{a_{i, j}, b_{i, j}} \in \mathcal{T}$이다.
3. $U_{a_i, b_i} \cap U_{a_j, b_j}$는 공집합이거나, 어떤 정수 $c, d$에 대해 $U_{c, d}$와 같다. 
   * $U_{a_i, b_i} \cap U_{a_j, b_j}$가 공집합이라면, 그냥 공집합이다. 
   * $T = U_{a_i, b_i} \cap U_{a_j, b_j}$가 공집합이 아니라면, $c = a_i + k_i b_i = a_j + k_j b_j$를 이 집합의 원소라고 하고, $d = m_i b_i = m_j b_j$는 $b_i, b_j$의 최소공배수라고 하자. 이때 $T = U_{c, d}$임을 보이자. $x \in T$이면 어떤 정수 $n_i, n_j$에 대해 $x = a_i + n_i b_i = a_j + n_j b_j$이다. $x - c = (n_i - k_i) b_i = (n_j - k_j) b_j$이므로 $x - c$는 $b_i, b_j$의 배수이고, 따라서 $d$의 배수이다. $x = c + yd$를 만족하는 정수 $y$가 존재하므로 $x \in U_{c, d}$이고, 따라서 $T \subset U_{c, d}$이다. $c + nd \in U_{c, d}$이면 $c + nd = a_i + (k_i + n m_i) b_i \in U_{a_i, b_i}$, $c + nd = a_j + (k_j + n m_j) b_j \in U_{a_j, b_j}$이므로 $c + nd \in T$이고 $U_{c, d} \in T$이다.
  
   두 경우 모두 $V_{i, j} = U_{a_i, b_i} \cap U_{a_j, b_j}$는 $\mathbb{Z}$의 열린 집합이다.
   두 열린 집합 $\bigcup_{i_1 \in I_1} U_{a_{i_1}, b_{i_1}}$, $\bigcup_{i_2 \in I_2} U_{a_{i_2}, b_{i_2}}$의 교집합 $\bigcup_{(i_1, i_2) \in I_1 \times I_2} V_{i_1, i_2}$는 열린 집합이다. 


이 위상에서 부분집합 $U$가 열린집합임과 닫힌집합임은 동치이다. 또한, 공집합이 아닌 열린집합은 항상 무한집합이다. 소인수분해의 존재에 의해, $\bigcup_{p \in \Pi} U_{0, p} = \mathbb{Z} \setminus \{-1, 1\}$이다. $\{-1, 1\}$은 유한집합이므로 열린집합이 아니고, 특히 $\mathbb{Z} \setminus \{-1, 1\}$은 닫힌집합이 아니다. $\Pi$가 유한하다고 가정하면 좌변은 닫힌집합의 유한합집합이므로 닫힌집합이고, 이때 등식은 닫힌집합과 닫히지 않은 집합이 같음을 의미하므로 (즉 어떤 집합 $U \subset \mathbb{Z}$에 대해 $\mathbb{Z} \setminus U \in \mathcal{T}$와 $\mathbb{Z} \setminus U \not\in \mathcal{T}$를 동시에 함의하므로) 모순이다. 

## FLT와 Schur의 정리를 이용한 증명

놀랍게도 페르마의 마지막 정리와 Schur의 정리가 참이면 소수는 무한히 많이 존재한다. 알려져 있는 FLT의 증명에서 소수의 무한성을 가정하는지는 모르겠다.

