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

# 1. 기본 행 연산

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

정확하게는, 항등 행렬(Identity Matrix) 에 기본 행 연산을 취하고
이를 우리가 원하는 행렬 왼쪽에다가 곱하면 같은 결과를 얻는다.

이떄 항등 행렬에 기본 행 연산을 시행한 결과를 기본 행렬(Elementary Matrix) 라고 하며 밑 예시에서

기본 행 연산의 종류에 따라 E 밑에 첨자를 붙여 구분하겠다.

$$ A = 
\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
$$ 

라고 놓고 그 결과를 확인해보자.

1. 한 행과 다른 행을 서로 맞바꾼다. 
$$ E_1A =
\begin{bmatrix}
0 & 1 & 0 \\
1 & 0 & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
=
\begin{bmatrix}
d & e & f \\
a & b & c \\
g & h & i
\end{bmatrix}
$$
1. 한 행에 0이 아닌 상수를 곱한다.
$$ E_2A =
\begin{bmatrix}
2 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
=
\begin{bmatrix}
2a & 2b & 2c \\
d & e & f \\
g & h & i
\end{bmatrix}
$$
1. 한 행에 0이 아닌 상수를 곱하고 이를 다른 행에 더한다.
$$ E_3A =
\begin{bmatrix}
1 & 0 & 0 \\
2 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
=
\begin{bmatrix}
a & b & c \\
2a+d & 2b+e & 2c+f \\
g & h & i
\end{bmatrix}
$$

이렇게 기본 행렬을 곱하는 것으로 연립방정식을 푸는 과정을

행렬로 표현할 수 있으며, 이를 이용하여 LU 분해를 시작할 수 있다.


# 2. LU 분해

# 3. 숄레츠키 분해(Cholesky Decomposition)