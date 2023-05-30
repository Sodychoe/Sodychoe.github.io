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

파이썬은 함수 자체도 인자로 넣는 것을 허용하는데 이를 이용한 것이다.

<script src="https://gist.github.com/Sodychoe/dac37247277d00d4b24be15d2e08925b.js"></script>

데코레이터는 다른 함수를 감싸 추가 기능을 부여하는 함수라고 생각하면 쉽다.

스크립트를 보면, 우리가 사용하고 싶은 say_hello 라는 함수를 데코레이터 함수의

인자로 넣는다. 그리고 이것을 wraaper_function 함수로 감싸서 say_hello 

함수가 실행되기 전후에 원하는 기능을 넣어주면 된다.


# 3. @ 로 데코레이터 사용하기

<script src="https://gist.github.com/Sodychoe/1974388ecd29858aff19a6abe95bb76e.js"></script>

# 4. *args 와 **kwargs 이용하여 데코레이터 만들기

# 5. 시간 측정 데코레이터 만들기

# 5. 파이썬 클래스에서 사용하는 데코레이터 