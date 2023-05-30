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

그런데 프로그래밍에서 함수란 반복된 행동을 

데코레이터는 함수에 추가 기능을 부여하면서 원래 코드를 크게 수정하지 않고 싶을 때 사용할 수 있다.

# 2. 데코레이터 만들기

<script src="https://gist.github.com/Sodychoe/dac37247277d00d4b24be15d2e08925b.js"></script>

# 3. @ 로 데코레이터 사용하기

# 4. 파이썬 클래스와 데코레이터 