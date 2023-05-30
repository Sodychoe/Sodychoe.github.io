---
title:  "파이선 데코레이터 정리(Decorator)"

excerpt: python

toc : true
toc_sticky : true  

use_math: true

categories:
  - devops
tags:
  - devops
  - python
  - decorator
---

파이썬의 데코레이터에 대해서 알아본다.

# 1. 개요

함수의 실행 시간을 측정하려면 흔히 사용하는 방법은 함수의 시작 부분과 끝 부분에
time 라이브러리의 메소드를 사용하는 것이다.

그런데 함수마다 실행 시간을 알기 위해 이 작업을 하는 것은 매우 귀찮다.
이럴 때 사용할 수 있는 것이 바로 파이썬의 데코레이터다.

데코레이터는 함수에 추가 기능을 부여하면서 원래 코드를 크게 수정하지 않고 싶을 때 사용할 수 있다.

# 2. 데코레이터 만들기

데코레이터 함수 형태는 다음과 같다.

<script src="https://gist.github.com/Sodychoe/dac37247277d00d4b24be15d2e08925b.js"></script>

데코레이터는 다른 함수를 감싸 추가 기능을 부여하는 함수라고 생각하면 쉽다.

# 3. @ 로 데코레이터 사용하기

# 4. 파이썬 클래스와 데코레이터 