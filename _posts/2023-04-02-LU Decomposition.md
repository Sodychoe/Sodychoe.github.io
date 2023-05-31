---
title:  "LU Decomposition"

excerpt: Computational Statistics, Matrix Factorization, LU decomposition 

toc : true
toc_sticky : true  

use_math: true

categories:
  - study
tags:
  - study
  - Computational Statistics
  - Matrix Factorization
  - LU Decomposition
---

자연수에는 약수라는 개념이 있고, 다항식에는 인수분해라는 개념이 있다.

이것은 어느 한 원소를 곱셈이라는 연산으로 나타내는 것이다.

행렬에서도 이러한 개념이 존재하고, 이를 보통 행렬의 분해(Decomposition) 이라고 한다.

이 글에서는 유명한 행렬 분해 방법 중 하나인 LU 분해(LU Decomposition) 에 대해서 다룬다. 


우선 행렬을 다른 행렬들의 곱으로 표기할 수 있다는 아이디어의 출처부터 찾아보도록 하자.

선형대수학 첫 시간에 행렬을 다루게 되면 행렬과 연립방정식을 비교하면서 기본 행 연산을
(Elementary Row Wise Operation) 다루게 되는데
이는 다음과 같다. 

1. 한 행과 다른 행을 서로 맞바꾼다.
2. 한 행에 0이 아닌 상수를 곱한다. 
3. 한 행에 0이 아닌 상수를 곱하고 이를 다른 행에 더한다. 

잘 보면, 우리가 연립방정식을 풀 때, 미지수를 소거하기 위해서 방정식에
상수를 곱하거나 다른 식에 더해주는 것과 같은 행동을 행렬의 관점에서
진행하고 있는 것을 알 수 있다. 

**이는 행렬을 연립방정식을 나타내는 하나의 관점이라는 측면에서 접근한 것이다.**

그런데 재미있게도 한 행에 곱셈을 해주거나, 다른 행과 더하는 행위는
**행렬의 곱셈** 으로 표현할 수 있다. 

1. 한 행과 다른 행을 서로 맞바꾼다. 
$$ I =
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
2. 한 행에 0이 아닌 상수를 곱한다.
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
3. 한 행에 0이 아닌 상수를 곱하고 이를 다른 행에 더한다.
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}