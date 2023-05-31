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

t는 보통 시간을 나타낸다. 이떄,

1. 집합 T가 가산이면 이때의 확률 과정은 discrete-time 확률 과정
2. 집합 T가 연속이면 continuous-time 확률 과정

이라고 한다.

# 2. 셈 과정(Counting Process)

확률 과정 $$\{N(t), t \geq 0 \}$$ 이 다음을 만족하면 이를
Counting Process 라고 부른다. 

1. $$N(t) \geq 0$$.
2. $$N(t)$$ 는 정수 값을 가진다.
3. $$s<t \implies N(s) \leq N(t)$$.
4. $$s<t \quad$$ 일 때, $$N(t)-N(s)$$ 는 구간 (s, t] 에서 발생하는 사건의 수와 같다.

# 3. 포아송 과정(Poisson Process) 

# 4. References

1. Ross, Sheldon M. Stochastic processes. John Wiley & Sons, 1995.