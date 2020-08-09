---
layout: post
cover: 'assets/RAPIDS/Main.png'
title: 02. Data Science With RAPIDS Cupy Part 01
published: true
date: 2020-08-09 22:00:00
tags: [RAPIDS ,Python, Machine Learning,DataScience, Cupy, cupy , Data, Data Science]
author: Lee Je Young
---

# 02. Data Science With RAPIDS Cupy Part 01 - 기초
---
  <br><br>
  
  안녕하세요, 두번째 챕터 Cupy Part 01입니다.

  오늘은 Cupy의 기초부터 시작하도록 하겠습니다.

  그리고 코드위주로 작성할 예정이기 때문에 원본코드를 먼저 첨부하겠습니다.

  [원본코드 보러가기](https://github.com/Ign0reLee/Data_Science_With_RAPIDS/blob/master/Chapter%2002.Cupy/Cupy%20Part-01.ipynb)

  <br><br>


## Cupy?
---

  <br><br>

  Cupy란 무엇일까요?
  
  대부분의 사람들의 경우 python에서 수학적인 계산을 할 때 Numpy를 많이 사용할 것이라고 생각합니다.

  Numpy는 훌륭하고, 빠르고, 편하고, 좋은 라이브러리입니다.

  하지만 CPU에서 돌아간다는 점 때문에 대규모 작업을 처리할 때 작업시간이 조금 부담스러울 때가 있습니다.

  Cupy란, Python에서 NVIDIA CUDA를 사용한 가속화 컴퓨팅을 제공하는 오픈소스 라이브러리입니다.

  Cupy는 Numpy를 뛰어 넘는 속도를 보여주다고합니다.

  심지어, 자체 테스트에선 연산이 100배 이상 차이나는 경우도 있었다고 합니다.

  RAPIDS에서 제공하는 자체 Bechmark 기사를 같이 첨부하겠습니다.

  [Single-GPU Cupy Speedups](https://medium.com/rapids-ai/single-gpu-cupy-speedups-ea99cbbb0cbb)

  그렇다면 이런 Cupy는 어떻게 사용하는 걸까요?

  주피터 노트북 환경에서, 쉘별로 확인해보도록 하겠습니다.

  <br><br>

## Import 하기
---
  ```python
  import cupy as cp
  import numpy as np
  ```

  <br><br>

  이번 과정에서는 항상 Numpy와 Cupy 모두를 Import 할 예정입니다.

  실제 환경에서는 Numpy를 Cupy로 바꾸는 것 만으로 대부분의 코드가 포팅 가능하게 됩니다.

  왜냐하면 Numpy와 Cupy는 Method가 동일하기 때문입니다.

  하지만 실제론 조금 다른 부분도 있습니다. 중요한 부분은 이번 챕터에서 보고 넘어가도록 하겠습니다.

  <br><br>

## Simple Test Code
---

  간단한 코드를 통해 사용법을 보도록하겠습니다.

  먼저 Numpy 버전 코드입니다.
  ```python
  %time

  x_num = np.arange(6).reshape(2,3).astype("f")
  print("X : ", x_num)
  print("X sum : ", x_num.sum(axis=1))

  !nvidia-smi
  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/CPUTest.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  <br><br>

  다음은 Cupy 버전 코드입니다.
  ```python
  %time

  x_cp = cp.arange(6).reshape(2,3).astype('f')
  print("X : " , x_cp)
  print("X sum : ", x_cp.sum(axis=1))

  !nvidia-smi
  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/GPUTest.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  <br><br>

  지난번에 보았던 설치 부분에서도 봤던 코드와 유사합니다.

  결과 출력된 화면을 보면, GPU메모리가 올라간게 보이시나요?

  GPU에 Array가 올라갔음을 알 수 있습니다.

  <br><br>

## Time
---
  
  그런데 한가지 이상한 점이 있습니다.

  Numpy보다 빠르다고 이야기를 했는데, 위의 코드에서는 Numpy가 Cupy보다 동작 시간이 더 짧음을 볼 수 있습니다.

  어째서 Numpy의 동작 시간이 더 빨랐을까요?

  지금의 경우에는 연산량이 작기 때문입니다.

  무슨 이야기냐면, GPU는 항상 CPU보다 빠른것이 아닙니다.

  다음과 같은 상황에서는 CPU가 GPU보다 빠른 성능을 낼 수도 있습니다.

  1. 계산량이 충분하지 않은 경우
  <br>
  1. 잘못된 구조로 GPU 아키텍쳐를 만들었을 경우
  <br>
  1. (쉘 동작 시간에서는)처음 호출하는 경우

  지금의 경우 3번과 1번에 해당하는 상황인 것 같습니다.

  자 그러면 실제로 연산량이 많을수록 Cupy가 동작시간이 더 짧은지 코드로 확인해보겠습니다.


## Computing Time Test
---

  <br><br>

  지금 부터 간단하게 연산 시간 테스를 해보겠습니다.

  랜덤하게 생성한 N * N 크기의 행렬을 두개 만든 후, 내적을 실행해보겠습니다.

  그리고 N의 크기를 증가 시켜가면서 속도를 테스트 해 볼 예정입니다.

  직접 하셔도 좋고, 결과만 보고 가셔도 괜찮습니다.
  
  <br><br>

  ### Case 1. n=100

  ```python

  %time

  a = np.random.rand(n,n)
  b = np.random.rand(n,n)
  result = np.matmul(a,b)

  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case1_cpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br>

  ```python

  %time

  a = cp.random.rand(n,n)
  b = cp.random.rand(n,n)
  result = cp.matmul(a,b)

  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case1_gpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br><br>
  
  ### Case 2. n=1000

  ```python

  %time

  a = np.random.rand(n,n)
  b = np.random.rand(n,n)
  result = np.matmul(a,b)

  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case2_cpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br>

  ```python

  %time

  a = cp.random.rand(n,n)
  b = cp.random.rand(n,n)
  result = cp.matmul(a,b)
  
  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case2_gpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br><br>

  ### Case 3. n=10000

  ```python

  %time

  a = np.random.rand(n,n)
  b = np.random.rand(n,n)
  result = np.matmul(a,b)

  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case3_cpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br>

  ```python

  %time

  a = cp.random.rand(n,n)
  b = cp.random.rand(n,n)
  result = cp.matmul(a,b)
  
  ```
  <amp-img src="{{ site.baseurl }}assets/RAPIDS/Cupy-01/case3_gpu.png" width="656" height="50" layout="responsive" alt="" class="mb3"></amp-img>
  <br>

  확실히 연산량이 늘어나면 늘어날수록 Numpy에 비해 Cupy가 훨씬 빠른 속도를 냄을 알 수 있습니다.

  반면 n이 작을땐, Numpy가 속도가 더 빠른걸 볼 수 있습니다.

  <br><br>
  
