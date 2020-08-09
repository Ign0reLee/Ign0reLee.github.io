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
  
  <br><br>

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
  
  <br><br>

  간단한 코드를 통해 사용법을 보도록하겠습니다.

  먼저 Numpy 버전 코드입니다.

  <br><br>

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

  <br><br>

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

  
