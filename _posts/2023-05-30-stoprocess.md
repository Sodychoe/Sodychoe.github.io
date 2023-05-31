---
title:  포아송 과정

excerpt: Stochastic Process  

toc : true
toc_sticky : true  

use_math: true

categories:
  - study
tags:
  - study
  - stochastic_process
---

# 1. 확률 과정(Stochastic Process)
확률 과정 $$\mathbf{X} = \{X(t), t \in T\}$$ 은
확률 변수들의 Collections 이다. 이 말은 각 t에 대하여 $$X(t)$$ 는 확률 변수라는 의미가 된다.

t는 보통 시간을 나타낸다. 이때,

1. 집합 T가 가산이면 이때의 확률 과정은 discrete-time 확률 과정
2. 집합 T가 연속이면 continuous-time 확률 과정

이라고 한다.

# 2. 셈 과정(Counting Process)

확률 과정 $$\{N(t), t \geq 0 \}$$ 이 다음을 만족하면 이를
Counting Process 라고 부른다. 

이때 $$N(t)$$ 를 시간 t 까지 발생한 사건의 총 개수로 생각할 수 있다.

1. $$N(t) \geq 0$$.
2. $$N(t)$$ 는 정수 값을 가진다.
3. $$s<t \implies N(s) \leq N(t)$$.
4. $$s<t \quad$$ 일 때, $$N(t)-N(s)$$ 는 구간 (s, t] 에서 발생하는 사건의 수와 같다.

**Independent Increments** 성질은 다음과 같다.

겹치지 않는 시간 구간에서 발생한 사건의 횟수는 서로 독립이다.

즉, $$N(t) \perp N(t+s)-N(t)$$

 **Stationary Increments** 성질은 다음과 같다.

어떤 시간 구간에서 발생하는 사건의 개수는 오로지 시간 구간의 길이에만 의존한다. 


# 3. 포아송 과정(Poisson Process) 

Counting Process $$\{N(t), t \geq 0 \}$$ 가 다음을 만족하면
이를 rate $$\lambda$$ 를 가지는 Poisson Process 라고 한다. 

1. $$N(0)=0$$.
2. Independent Increments 성질을 갖는다.
3. $$\forall s,t \geq 0, P\{N(t+s)-N(s)=n\}=e^{\lambda t}\frac{(\lambda t)^{n}}{n!}, \hspace{4mm} n=0,1,2 \cdots,$$.

여기서 3번 조건은 stationary increments 를 의미한다.

동치조건은 다음과 같다. 

1. $$N(0)=0$$.
2. Counting Process 는 stationary and independent increments 성질을 갖는다.
3. $$P\{N(h)=1\}=\lambda h+ o(h)$$.
4. $$P\{N(h) \geq 2\} = o(h)$$\\.

여기서 o(h) 는 little-o notation 을 의미한다.

증명은 다음과 같다. $$P_n(t) = P\{N(t)=n\}$$ 이라고 놓으면,

$$
\begin{align}
P_0(t+h) &= P\{N(t+h)=0\}  \\
&= P\{N(t)=0, N(t+h)-N(t)=0\} \hspace{4mm} \because \text{definition of the counting process}  \\
&= P\{N(t)=0\}P\{N(t+h)-N(t)=0\} \because \text{independent increments}  \\
&= P_0(t)[1-\lambda h + o(h)] \because \text{assumption 3,4]}
\end{align}
$$
양변을 h로 나누고 정리하면 다음과 같다.

$$\frac{P_0(t+h)-P_0(t)}{h}=\lambda P_0(t)+ \frac{o(h)}{h}.$$
이제 미분계수의 정의와 o(h) 의 정의에 따라 이 식은 h가 0으로 한없이 가까워 질 때, 다음과 같다.

$$P'_0(t)=- \lambda P_0(t)$$

이 미분 방정식을 풀면 (상수 조건 : N(0)=0) $$P_0(t)=e^{- \lambda t}$$ 가 된다.

$$n \geq 1$$ 일 때에는, 

$$
\begin{align}
P_n(t+h) &= P\{N(t+h) = n \} \\
&= P\{N(t)=n, N(t+h)-N(t)=0\}
\end{align}
$$



# 4. References

1. Ross, Sheldon M. Stochastic processes. John Wiley & Sons, 1995.