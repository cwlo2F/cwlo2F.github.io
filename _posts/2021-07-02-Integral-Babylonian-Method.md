---
layout: post
title: Integral Babylonian Method
tags:
  - Analysis
  - Problem-Solving
mathjax: true
date: 2021-07-02 03:16:07
---


# 바빌로니아 법

**바빌로니아 법**<sup>The Babylonian method</sup>은 임의의 수의 제곱근에 빠르게 수렴하는 수열을 통해 근사값을 얻는 방법이다. 임의의 양의 실수 $a \in \mathbb{R}_{> 0}$에 대해, 다음과 같은 수열을 구성하여 <span>$\sqrt{a}$</span>의 근삿값을 구할 수 있다.
1. 임의의 양의 실수 $x_0$를 택한다. 예컨대 $x_0 = a$와 같이 택할 수 있다.
2. $n \in \mathbb{Z}_{\ge 0}$에 대해, $x_{n + 1} = \frac{1}{2} \left( x_n + \frac{a}{x_n} \right)$을 계산한다.
3. 원하는 정밀도에 이르기까지 2의 과정을 반복한다.

위의 방법을 따라 $x_0 = 2$를 택하여 $\sqrt{2}$를 근사하는 과정은 다음과 같다.
$$\begin{align*}
x_0 & = 2 \\
x_1 & = \frac{1}{2} \left( 2 + \frac{2}{2} \right) = \frac{3}{2} = 1.5 \\
x_2 & = \frac{1}{2} \left( \frac{3}{2} + \frac{2 \cdot 2}{3} \right) = \frac{17}{12} \approx 1.416666666666667 \\
x_3 & = \frac{1}{2} \left( \frac{17}{12} + \frac{2 \cdot 12}{17} \right) = \frac{577}{408} \approx 1.41421568627451 \\
x_4 & = \frac{1}{2} \left( \frac{577}{408} + \frac{2 \cdot 408}{577} \right) = \frac{665857}{470832} \approx 1.41421356237469 \\
\vdots
\end{align*}$$
$\sqrt{2} \approx 1.414213562373095$이므로 이 수열은 $\sqrt{2}$를 근사하는 것처럼 보인다.

이 글에서는 바빌로니아 법이 왜 양의 실수의 제곱근을 근사하는지 알아보고, 이를 problem-solving에서 활용하는 방법에 대해 소개한다.

# 바빌로니아 법 증명하기

양의 실수 $a$와 실수 $x_0 = r$에 대해, 바빌로니아 법을 사용하여 얻은 수열 $x_0, x_1, x_2, \cdots$를 **$r$에서 시작한 $\sqrt{a}$를 근사하는 바빌로니아 수열**, 또는 $a$가 맥락에서 명백할 경우 **$r$에서 시작한 바빌로니아 수열**이라고 하자. 

임의의 실수 $x_0$으로 시작한 $\sqrt{a}$를 근사하는 바빌로니아 수열 $x_n$에 대해, $x_n = \sqrt{a}(1 + \varepsilon_n)$을 만족하도록 새로운 변수 $\varepsilon_n = \frac{x_n}{\sqrt{a}} - 1$을 정의하자. 다음과 같은 $\varepsilon_n$에 대한 점화식을 얻을 수 있다.
$$\begin{align*}
\varepsilon_{n + 1} & = \frac{x_{n + 1}}{\sqrt{a}} - 1 \\
& = \frac{1}{2\sqrt{a}} \left(x_n + \frac{a}{x_n} \right) - 1 \\
& = \frac{1}{2\sqrt{a}} \left( \left(x_n - \sqrt{a} \right) + \frac{\sqrt{a}}{x_n} (\sqrt{a} - x_n) \right) \\
& = \frac{1}{2\sqrt{a}} \sqrt{a} \varepsilon_n \left(1 - \frac{\sqrt{a}}{x_n} \right) \\
& = \frac{1}{2} \frac{\varepsilon_n^2}{1 + \varepsilon_n}
\end{align*}$$
$\varepsilon_n = \frac{x_n}{\sqrt{a}} - 1 > -1$임을 관찰하자. 모든 $n \ge 1$에 대해 $\varepsilon_n$은 양수이고, 점화식으로부터 $\varepsilon_{n + 1} \le \min\left\{ \frac{\varepsilon_{n}^2}{2}, \frac{\varepsilon_n}{2} \right\}$를 만족한다. 임의의 $M > 1$에 대해, $m$이 충분히 클 때 $\varepsilon_m < \frac{1}{M}$이므로, 이러한 $\varepsilon_m$에서 시작하는 바빌로니아 수열에 대해 $\varepsilon_{m + n}$은 $\mathcal{O}(M^{-2^n})$이다. $0 \le \lim\limits_{n \to \infty} \varepsilon_n \le \lim\limits_{n \to \infty} M^{-2^n} = 0$이므로 $\varepsilon_n \to 0$이고, 바빌로니아 수열 $x_n = \sqrt{a}(1 + \varepsilon_n)$는 $\sqrt{a}$로 수렴한다.

# 정수 바빌로니아 법

이 글의 제목인 "정수 바빌로니아 법"<sup>The integral Babylonian method</sup>은 임의로 지어낸 말로, problem-solving에서 간간히 필요로 하는 계산인 음이 아닌 정수의 제곱근의 바닥<sup>floor</sup>을 구하는 방법이다. 가급적이면 실수 계산을 피하고 싶어 만들게 되었는데, 이 절에서 정수 자료형과 바빌로니아 법을 사용하여 음이 아닌 정수의 제곱근의 바닥을 계산하는 C++ 함수와 그 정당성의 증명을 제시한다.

## 정수 바빌로니아 법의 C++ 구현

다음 `integral_babylonian` 함수는 정수형 입력 $n$에 대해 $n$이 음이 아닌 정수라면 $\left \lfloor \sqrt{n} \right \rfloor$를 계산하여 반환한다. $n$이 음의 정수라면 $-1$을 반환한다.

```c++
int integral_babylonian(int n) {
    if (n < 0) return -1;
    if (n == 0) return 0;
    int p = n, x = (n + 1) / 2;
    while (p > x) p = x, x = (x + n / x) / 2;
    return p;
}
```

왜 이런 코드가 나왔는지 모르겠지만 어쨌든 잘 동작한다.

## 정당성과 시간 복잡도

위 알고리즘은
$$x_0 = N, \quad x_{n + 1} = f(x_n; N) := \left\lfloor \frac{1}{2} \left( x_n + \left\lfloor \frac{N}{x_n}\right\rfloor \right) \right\rfloor $$
으로 정의되는 수열을 계산한다.

$N = 0$일 때, 함수는 0을 반환한다. 이는 원하는 결과이다.

$N = 1$일 때, $f(1; 1) = 1$이므로 `while` 구문 내의 코드가 한 번 실행된 후 1을 반환한다. 이는 원하는 결과이다.

양의 정수 $N$에 대해, $M = \left\lfloor \sqrt{N} \right\rfloor$이라고 하자. 양의 정수 $e \ge 1$에 대해 $x = M + e$라고 쓸 수 있을 때, $\left\lfloor \frac{1}{2} \left( x + \left\lfloor \frac{N}{x}\right\rfloor \right) \right\rfloor$는 더 작은 오차를 가짐을 보일 것이다.

$N > 1$일 때 $\sqrt{N} < N$이므로 $M < N$이다. 따라서 첫 번째 항은 $x = M + e_0$, $e_0 = N - M$과 같이 쓸 수 있다.

$(M - e)(M + e) = M^2 - e^2 < M^2 \le N$이므로, $M - e < \frac{N}{M + e}$이고, $M - e \le \left\lfloor \frac{N}{M + e} \right\rfloor$이다. $M \le \sqrt{N} < M + 1$이므로, $N < (M + 1)^2$이고, $\left\lfloor \frac{N}{x} \right\rfloor \le \frac{N}{M + e} \le \frac{N}{M + 1} < M + 1$이다.
$$\begin{align*}
f(M + e; N) & \le \frac{1}{2} \left(M + e + \left\lfloor \frac{N}{M + e}\right\rfloor \right) \\
& < \frac{1}{2} (M + e + M + 1) = M + \frac{e + 1}{2}
\end{align*}$$
이다. 또한 $M + e + \left\lfloor \frac{N}{M + e}\right\rfloor \ge M + e + M - e = 2M$이므로 $f(M + e; N) \ge M$이고, 계산 결과는 $M + e'$, $e' \ge 0$과 같이 나타낼 수 있다. 오차의 상한 $e_{n + 1} = \frac{e_n + 1}{2}$의 일반항은 $e_n = \frac{e_0}{2^n} + \frac{2^n - 1}{2^n} < \frac{e_0}{2^n} + 1$이고, 이는 $1$으로 수렴한다. 따라서 $x \leftarrow f(x; N)$을 반복하다 보면 $M$ 또는 $M + 1$에 도달하게 된다.

$M^2 \le N < M^2 + 2M$인 경우, $x \leftarrow f(x;N)$은 $M$으로 도달하고, $f(M + 1; N) = f(M; N) = M$이 성립한다. $N = M^2 + 2M$일 때,
$$f(M; M^2 + 2M) = M + 1, f(M + 1; M^2 + 2M) = M$$
위 계산이 고리를 만들게 된다. `while`문의 조건을 `p > x`와 같이 씀으로써 $p = M, x = M + 1$인 경우에 탈출할 수 있다.

알고리즘 정당성에서 사용한 부등식 $e_n \le \frac{N - M}{2^n} + 1$을 사용하면, $f(-; M)$를 $N$에 $\mathcal{O}(\log N)$번 취하였을 때 $M$을 얻을 수 있음을 알 수 있다. 따라서 정수 바빌로니안 법의 시간 복잡도는 $\mathcal{O}(\log N)$이다.



## 정수 바빌로니아 법의 효용

naïve한 선형 탐색은 $\mathcal{O}(\sqrt{N})$ 시간 복잡도를 갖는다. 정수 바빌로니아 법은 $\mathcal{O}(\log n)$ 시간 복잡도를 가지므로 선형 탐색보다 빠르게 수행될 수 있다.

이분 탐색을 사용해도 $\mathcal{O}(\log n)$ 시간 복잡도로 음이 아닌 정수의 제곱근의 바닥을 계산할 수 있다. 
```c++
int sqrt_floor(int n) {
    if (n < 0) return -1;
    int l = 0, r = n + 1;
    while (l + 1 < r) {
        int m = (l + r) / 2;
        if ((long long) m * m > N) l = m;
        else r = m;
    }
    return l;
}
```
이 이분 탐색은 $[l, r)$ 구간에서 적당히 중간값인 $m = (l + r) / 2$에 대해 $m^2$과 $n$의 크기를 비교하여 $\left\lfloor \sqrt{n} \right\rfloor$이 $[l, m)$ 와 $[m, r)$ 중 어디에 포함되는지를 판정하는 것을 반복한다. `m * m`을 계산할 때 오버플로우가 발생할 수 있음에 주의하자.

이분 탐색은 편리하고 범용성이 있지만, 제곱근 바닥을 계산하기 위해서 정수 바빌로니아 법을 사용하였을 때 다음과 같은 효용이 있을 것이다. 첫째로, 계산 식이 `x = (x + n / x) / 2;`와 같이 간단하기 때문에 구현을 암기하기 쉽다. 또한, `m`의 제곱을 계산할 때 발생할 수 있는 오버플로우 문제 또는 이분 탐색에서 흔히 범하는 탐색 범위를 설정하는데 발생할 수 있는 실수를 피할 수 있을 것이다. 그러나 여전히 `while`문의 조건을 헷갈릴 수 있다.