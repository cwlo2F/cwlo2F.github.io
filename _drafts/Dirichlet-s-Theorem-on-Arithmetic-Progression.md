---
title: Dirichlet's Theorem on Arithmetic Progression [wip]
tags: Number-Theory
mathjax: true
date: 2021-06-24 10:00:00
update: 2022-05-24 03:00:00
---

# 서문

이 글은 기초적인 정수론, 집합과 함수 개념, 수열의 극한 그리고 복소수체 $\mathbb{C}$가 어떻게 생겨먹었는지 알고 있고, 한국어를 사용하며, 수학에 관심이 있는 고등학생 또는 대학생을 예상 독자로 가정하여 등차수열에 대한 디리클레 정리와 그 증명을 소개하기 위해 써졌다. 영어 수학 용어에 익숙한 독자들을 위해 주관적인 기준으로 생소하거나 이 글 이외에서 사용처를 찾기 힘든 한국어 용어에는 윗첨자 표기를 통해 대응되는 영어 용어를 함께 제시하였다.

2021년 6월 29일의 감상: 단순히 [1]을 번역하는 작업이 되고 있는 것은 아닐까? 현재는 해석학에 관한 많은 배경 지식을 함께 서술하려고 시도하고 있는데, 아직 다 쓰지는 않았지만 글이 점점 무거워지는 것을 느낀다. 고등학생 독자를 위해 필요 없는 것(군에 대한 설명 등)은 쳐낼 수 있으면 좋을 것이다.

첫 절인 소수의 무한성은 재미있기는 하지만 이 글에서 꼭 필요한 요소일지는 잘 모르겠다.

2022년 5월 24일의 감상: 무언가 더 나아지지는 않았는데, 해석학 공부를 좀 더 한 뒤 작성을 계속하고 싶다.

## 소수의 무한성

### 소수

**소수**는 그 양의 약수가 1과 자기 자신 이외에 존재하지 않고 1보다 큰 양의 정수이다. 예컨대, 7의 양의 약수는 1과 7이고 그 밖에 양의 약수는 존재하지 않으므로 7은 소수이다. 한편, 3은 57 = 3·19 의 양의 약수이다. 57은 소수가 아니다. 1보다 크고 소수가 아닌 양의 정수를 **합성수**라고 부른다. 57은 합성수이다.

주제에 대한 이야기를 시작하기 이전에, 소수가 무한히 많이 존재한다는 것에 대해 이야기할 것이다. 이 명제를 **소수의 무한성**<sup>**infinitude of primes**</sup>이라고 한다. 


**보조정리** 1보다 큰 모든 양의 정수에 대해, 두 번째로 작은 양의 약수는 소수이다.

**증명** 결론을 부정하여, 두 번째로 작은 양의 약수가 소수가 아닌 양의 정수가 존재한다고 가정하자. $n > 1$을 그 중 가장 작은 것이라고 하자. $m$을 $n$의 두 번째로 작은 양의 약수라고 하자. 1은 가장 작은 $n$의 양의 약수이므로, $m$은 1보다 크다. 만약 $m = n$이라면, 1과 $m = n$ 사이에는 다른 $n$의 양의 약수가 존재하지 않고, 따라서 $m = n$은 소수인데 이는 $n$의 선택과 모순이다. 

$m < n$을 가정하자. $n$은 결론이 성립하지 않는 최소의 정수이므로, $m$의 두 번째로 작은 양의 약수는 소수이다. $p$를 $m$의 두 번째로 작은 양의 약수라고 하자. $p$는 $n$의 약수가 되는데, $p < m$이라면 $m$이 $n$의 두 번째로 작은 양의 약수라는 사실과 모순이다. 따라서 $p = m$이고, $m$은 소수이다. 그러나 $n$의 선택에 의해 $m$은 소수가 아니어야 하는데, 이는 모순이다. 따라서 보조정리는 참이다. Q.E.D.

**따름정리** 1보다 큰 모든 양의 정수는 소수인 약수를 갖는다.

$U$를 임의의 집합, $V$를 덧셈 항등원 0이 존재하는 대수 구조라고 하자. 함수 $f: U \to V$에 대해, $f$의 **받침**<sup>**support**</sup> $\mathrm{Supp}(f) \subset U$은 $\{x \in U: f(x) \neq 0\}$으로 정의된다. $f$가 **유한받침함수**<sup>**finitely supported function**</sup>라는 것은 $\mathrm{Supp}(f)$가 유한집합이라는 뜻이다. 유한받침함수에서는 무한합 $\sum_{x \in U} f(x)$ 등이 $\sum_{x \in \mathrm{Supp}(f)} f(x)$와 같이 잘 정의될 수 있다.

모든 소수로 이루어진 $\mathbb{Z}_{\ge 0}$의 부분집합을 $\Pi$라고 하자. 1보다 큰 양의 정수 $n$과 유한받침함수 $e: \Pi \to \mathbb{Z}_{\ge 0}$에 대해, 
$$\prod_{p \in \mathrm{Supp}(e)} p^{e(p)} = n$$
를 만족할 때 $e$를 $n$의 **소인수분해**라고 한다. 

**소인수 분해의 존재성** 1보다 큰 모든 양의 정수는 소인수 분해를 갖는다.

**소인수 분해의 유일성** 1보다 큰 양의 정수의 두 소인수 분해는 서로 같다.

소인수 분해에 관한 정리들의 증명은 어렵지 않고 여러 기초적인 정수론 자료에서 찾을 수 있으므로 생략한다.

### 유클리드<sup>Euclid</sup>의 증명

**소수의 무한성** 소수의 무한성은 참이다.

**유클리드의 증명** 결론을 부정하여 소수의 무한성이 거짓이라고 가정하자. $\Pi$를 모든 소수로 이루어진 $\mathbb{Z}$의 부분집합이라고 하자. 모든 소수의 곱에 1을 더한 수
$$P = 1 + \prod_{p \in \Pi} p$$
를 생각하자. $\Pi$는 유한집합이므로 $P$는 잘 정의된다. 모든 $p \in \Pi$에 대해 
$$p \le \prod_{p \in \Pi} p < 1 + \prod_{p \in \Pi} p = P$$
이므로, $P$는 $\Pi$에 포함되지 않는다. $q$를 $P$의 소수인 양의 약수라고 하자. $P$는 모든 $\Pi$의 원소 $p$에 대해, $P$를 $p$로 나누었을 때 나머지가 1이 남고, 1은 $p$의 배수가 아니므로 $p$는 $P$의 약수가 아니다. 따라서 $q \not\in \Pi$인데, 이는 보조정리에 의해 $q$가 소수가 되어야 한다는 점과 모순이다. 따라서 소수의 무한성은 참이다. Q.E.D.

## $a + nm$꼴 소수와 그 무한성 문제

정수 $a, m$에 대해, $x$가 $a + nm$꼴의 정수라는 것은, 어떤 음이 아닌 정수 $n$이 존재하여 $x = a + n \cdot m$을 만족한다는 뜻이다. 이는 $x$가 초항이 $a$이고 공차가 $m$인 등차수열에 등장한다는 것과 동치이다.

유클리드의 증명을 흉내내어 $3n + 2$꼴 소수의 무한성을 증명할 수 있다.

**$3n + 2$꼴 소수의 무한성** $3n + 2$꼴의 소수는 무한히 많이 존재한다. 즉, 초항이 2이고 공차가 3인 등차수열은 소수를 무한히 많이 포함한다.

**증명** 결론을 부정하여 $3n+2$꼴 소수의 무한성이 거짓이라고 가정하자. $\Pi_{2, 3}$를 모든 $3n + 2$꼴 소수로 이루어진 $\mathbb{Z}$의 부분집합이라고 하자. 모든 $3n + 2$꼴의 소수의 곱에 3을 곱하고 1를 뺀 수
$$P = -1 + 3 \prod_{i = 1}^n p_i = -1 + 3 \prod_{p \in \Pi_{2, 3}} p$$
를 생각하자. $\Pi_{2, 3}$는 유한집합이므로 $P$는 잘 정의된다. 모든 $p \in \Pi$에 대해 $p \ge 2$이므로
$$p < -1 + 3 \prod_{p\in \Pi_{2, 3}} = P$$
이고, $P$는 $\Pi_{2, 3}$에 포함되지 않는다. $q$를 $P$의 소수인 약수라고 하자. $P$는 모든 $\Pi_{2, 3}$의 원소 $p$에 대해, $P$를 $p$로 나누었을 때 -1이 나머지이다. $-1$은 $p$의 배수가 아니므로 $p$는 $q$의 약수가 아니다. 따라서 $q \not\in \Pi_{2, 3}$이고, $q$는 $3n + 1$꼴의 소수이다. $P$의 소인수분해를 생각하였을 때, $P$는 $3n + 1$꼴 소수들의 곱이다. $3n+1$꼴 정수의 곱은 다시 $3n+1$꼴 정수임을 관찰하자.
$$(3u + 1)(3v + 1) = 3(3uv + u + v) + 1$$
$P$는 $3n + 1$꼴 정수의 곱이므로 $3n+1$꼴 정수인데, $P = -1 + \prod_{p \in \Pi_{2, 3}} p$가 $3n + 2$꼴 수가 되도록 하는 구성과 모순이다. 따라서 $3n + 1$꼴 소수의 무한성은 참이다. Q.E.D.

$4n + 3$꼴의 소수가 무한히 많이 존재하는데, 이도 비슷한 구성을 통해 증명할 수 있다. 이는 곱셈군 $(\mathbb{Z}/n\mathbb{Z})^\times$이 충분히 작다는 데에서 기인하는 증명이므로 $m$이 클 때에는 같은 방법을 적용할 수 없다. 

이 글에서 다룰 디리클레 정리는 이러한 $a + nm$꼴 소수 무한성 문제를 해결한다.

# 등차수열에 대한 디리클레 정리

등차수열에 대한 디리클레 정리는 "자명하지 않은 $a + nm$꼴 소수의 무한성 문제는 항상 긍정적인 답을 갖는다"로 요약될 수 있다. 즉, 등차수열 $a + nm$에 무한히 많은 소수가 *명백히 존재하지 않도록* $a$와 $m$이 주어지지 않는 이상, 이 등차수열은 항상 무한히 많은 소수를 포함한다. 예컨대 다음 문장들은 참이다.
* $7n + 5$꼴 소수는 무한히 많이 존재한다.
* 마지막 네 자리가 1001인 소수, 즉 $10000n + 1001$꼴 소수는 무한히 많이 존재한다.

$a + nm$꼴 소수의 무한성 문제가 자명하다는 것은 무엇일까? $a$와 $m$이 서로소가 아닌 경우, 충분히 큰 모든 $n$에 대해 $a + nm$은 $a$와 $m$의 최대공약수로 나누어 떨어지므로 소수가 아닐 것이다. 이 경우, 무한성 문제는 *자명하게* 부정적인 답을 갖는다. 따라서 증명하고자 하는 정리는 다음과 같다.

**등차수열에 대한 디리클레 정리** $a$는 정수, $m$은 1보다 큰 정수일 때, $a$와 $m$이 서로소라면 $a + nm$꼴 소수는 무한히 많이 존재한다.

## 소수의 무한성: 에르되시의 증명

등차수열에 대한 디리클레 정리의 알려진 증명과 아이디어가 매우 밀접하다고 생각되어 소수의 무한성에 대한 에르되시의 증명을 소개한다. 수열 $\{p_n\}$에는 모든 소수가 정확히 한 번씩 등장하고, 임의의 $i < j$에 대해 $p_i < p_j$를 만족한다고 하자. 만약 소수의 무한성이 거짓이어서 소수가 정확히 $N \in \mathbb{Z}_{\ge 0}$개 존재할 경우, 모든 $i \in \mathbb{Z}_{\ge 1}$에 대해 $p_{N + i} = +\infty$로 정의하자. $\frac{1}{+\infty} = 0$으로 정의하자.

**모든 소수 역수의 합** 무한합 $\displaystyle\sum_{n = 1}^\infty \frac{1}{p_n}$는 발산한다.

**에르되시의 증명** 결론을 부정하여 $\displaystyle\sum_{n = 1}^\infty \frac{1}{p_n}$이 실수 $L$에 수렴한다고 가정하자. $\displaystyle\sum_{n = k + 1}^\infty \frac{1}{p_n} < \frac{1}{2}$를 만족하는 가장 작은 정수 $k$를 선택하자. $p_1 = 2$이므로 $k \ge 1$, 특히 $k \neq 0$임을 관찰하자. 또한 조건에서 $k$의 최소성에 의해 $k$번째 소수 $p_k$는 존재하고, 특히 $p_k \neq +\infty$임을 관찰하자. 양의 정수 $N$에 대해, $N$보다 작거나 같은 양의 정수 중 그 소인수분해 $e: \Pi \to \mathbb{Z}_{\ge 0}$가
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
을 얻는다. 이를 정리하면 $N \le 4^{k + 1}$인데, 이는 명백히 어떤 양의 정수에 대해 성립하지 않는 부등식이다. $N = 4^{k + 1} + 1$을 선택하여 위 논증을 반복하면 모순을 얻게 되므로, 무한합 $\displaystyle \sum_{n = 1}^\infty \frac{1}{p_n}$가 수렴한다는 가정은 잘못되었다. 따라서 무한합 $\displaystyle \sum_{n = 1}^\infty \frac{1}{p_n}$은 발산한다. Q.E.D.

*시덥잖은 글* cwlo2F는 위에서 사용된 무한합을 $\displaystyle\sum_{n = 1}^\infty \frac{1}{p_n}$ 대신 $\displaystyle\sum_{p \in \Pi} \frac{1}{p}$ 또는 $\displaystyle\sum_{p: prime} \frac{1}{p}$으로 쓰는 것이 좀 더 멋지다고 생각한다. 이는 절대수렴하지 않는 무한급수가 아니므로, $\Pi$에 $\mathbb{Z}$의 부분집합으로서의 대소관계에 의한 자연스러운 순서가 존재함에도 후자와 같은 표기는 지양하는 것이 좋다. 

## 곱셈군과 특성함수

1보다 큰 양의 정수 $n$에 대해, $(\mathbb{Z}/n\mathbb{Z})^\times$를 1이상 $n$이하의 정수 중 $n$과 서로소인 것으로 이루어진 집합이라고 하자. 이 집합 위에 곱셈을 $a \cdot b := ab \bmod n$으로 정의하면, $ab$는 $n$과 서로소이므로 $a \cdot b \in (\mathbb{Z}/n\mathbb{Z})^\times$이다. 

이렇게 집합 $G$와 집합 위의 연산 $\cdot: G \times G \to G$에 대해, 다음 세 공리를 만족하는 것을 **군**<sup>**group**</sup>이라고 한다. 통상적인 함수 표기를 사용한다면 연산 $\cdot$의 결과는 $\cdot(a, b)$처럼 적히지만, 연산 기호에 대해서는 특별히 연산 결과를 $a \cdot b$와 같이 쓰는 것을 허용한다. 
1. 임의의 $a, b, c \in G$에 대해 $(a \cdot b) \cdot c = a \cdot (b \cdot c)$이다. 
2. 어떤 $e \in G$가 존재하여 $a \cdot e = a = e \cdot a$이다. 이러한 원소 $e$를 **항등원**<sup>**identity**</sup>이라고 한다.
3. 임의의 $a \in G$에 대해 $x \in G$가 존재하여 $a \cdot x = e = x \cdot a$이다. $a \in G$에 대해 이러한 $x$는 유일하게 존재하고, $x = a^{-1}$와 같이 표기하며 이를 **$a$에 대한 역원**<sup>**inverse of $a$**</sup>이라고 한다.

위에서 정의한 집합 $(\mathbb{Z}/n\mathbb{Z})^\times$과 곱셈은 군을 이룸을 쉽게 확인할 수 있다. 3번 공리는 베주 항등식을 통해 검증할 수 있다. 

**법 $n$에 대한 특성함수**<sup>**character modulo $n$**</sup>는 곱셈을 보존하는 함수 $\chi: (\mathbb{Z}/n{\mathbb{Z}})^\times \to \mathbb{C}^\times$이다. 곱셈을 보존한다는 것은 임의의 $a, b \in (\mathbb{Z}/n{\mathbb{Z}})^\times$에 대해 $\chi(a \cdot b) = \chi(a) \cdot \chi(b)$가 성립함을 의미한다. 이러한 특성함수들 사이에서 곱셈을 
$$\chi_1 \cdot \chi_2(x) = x \mapsto \chi_1(x) \cdot \chi_2(x), \forall x \in (\mathbb{Z}/n\mathbb{Z})^\times$$
으로 정의하면 이 결과는 다시 특성함수가 된다. 모든 법 $n$에 대한 특성함수로 이루어진 집합을 $\widehat{G}$라고 하자.


## 증명 개요

$\Pi_{a, m}$을 모든 $a + nm$꼴 소수로 이루어진 $\mathbb{Z}$의 부분집합이라고 하자. "에르되시의 증명" 절에서 사용했던 표기를 빌려, 수열 $\{p_n\}$에는 모든 $a + nm$꼴 소수가 정확히 한 번씩 등장하고, 임의의 $i < j$에 대해 $p_i < p_j$를 만족하며, 만약 $a+nm$꼴 소수의 무한성이 거짓이면 첨자<sup>index</sup>가 충분히 큰 모든 항에 대해 $p_n = +\infty$라고 하자. 

증명의 핵심 아이디어는 무한합 $\displaystyle \sum_{n = 1}^\infty \frac{1}{p_n}$이 발산함을 보임으로써 $\Pi_{a, m}$가 무한집합임을 보이는 것이다. 여기에서 약간 문제가 생기는데, 이를 증명하기 위해 방대한 해석학, 특히 복소함수에 대한 해석학과 관련된 지식이 필요하다. 정말 그게 전부일 정도이다. 

등차수열에 관한 디리클레 정리는 해석적 정수론의 지평을 여는 결과이기도 하다. 다른 초등적인 증명이 존재할 수 있지만 위 아이디어를 사용하는 증명을 소개하기 위해 다음 절에서는 복소함수에 대한 해석학 개념, 용어, 정리를 소개할 것이다.


# 복소함수

작업 중.

## 복소함수 미분



## 함수열의 수렴

## 무한합과 복소함수

# 증명


## 제타함수

제타함수는 반평면 $\Re s > 1$위에서 다음과 같이 정의되는 함수이다.
$$\zeta(s) = \sum_{n = 1}^\infty \frac{1}{n^s}$$


천천히 작업 중. 마지막 업데이트: 2021-06-29

# 참고 문헌

[1] Jean-Pierre Serre, *A Course in Arithmetic*.
[2] Martin Aigner and Günter M. Ziegler, *Proofs from THE BOOK*.