---
layout: post
read_time: true
show_date: true
img: images/RAPIDS/Main.png
title: 03. Data Science With RAPIDS Cupy Part 02
published: true
date: 2020-08-19 22:00:00 0900
tags: [RAPIDS ,Python, Machine Learning, DataScience, Cupy, cupy , Data, Data Science]
author: Jeyoung Lee
mathjax: yes 
toc: yes 
---


  <br><br>
  
  안녕하세요, 두번째 챕터 Cupy Part 02입니다.

  오늘은 Cupy로 표현하는 선형대수학을 하도록 하겠습니다.

  마찬가지로 코드위주로 작성할 예정이기 때문에 원본코드를 먼저 첨부하겠습니다.

  [원본코드 보러가기](https://github.com/Ign0reLee/Data_Science_With_RAPIDS/blob/master/Chapter%2002.Cupy/Cupy%20Part-02.ipynb)

  <br><br>


## Cupy와 선형대수
---

  <br><br>

  선형 대수는 데이터 과학에서 기술과 개념을 뒷받침 해주는 분야입니다.

  이번 챕터에서는 Cupy를 이용한 선형 대수 표현을 배우겠습니다.

  실은 Cupy에서 이미 대부분의 선형대수의 개념을 함수로 만들어 놓았습니다.

  그래도 아직 익수하지 못한 분들을 위해, 그리고 처음 보는 분들을 위해 선형 대수 부분을 넣어두었습니다.

  따라서 앞서 배운 기초 부분과 많이 유사할 예정이며, 사용에 익숙하신 분들이라면 넘어가셔도 관계 없습니다.

  자 그럼 시작하겠습니다.

  주피터 노트북 환경에서, 쉘별로 확인해보도록 하겠습니다.

  <br><br>

## Import 하기
---
  <br>

  ```python
  import cupy as cp
  import numpy as np
  ```

  이번 칼럼에선 항상 numpy와 cupy를 임포트 해옵니다.

  다만, 이번 챕터에서는 시간에 대한 부분은 빠져있습니다.

  함수 사용에 관해 배울땐, 시간을 고려할 필요가 없기 때문입니다.

  <br><br>

## 2.1 벡터
---
<br>

### 2.1.0 벡터의 개념
---

  벡터와 스칼라는 수학을 공부해본 사람이라면 많이 보았을 개념일 것입니다.

  저는 수학과가 아니여서 그런지 벡터는 간단하게 방향이 있는 값 정도로 이해하고 있습니다.

  참고하고 있는 모 책에서는 __*어떤 유한한 차원의 공간에 존재하는 점들*__ 이라고 설명합니다.

  대부분의 숫자는 벡터로 표현 가능합니다.

  그리고 앞으로 많은 경우 이 벡터로 계산, 표현 할 예정입니다.

  그러므로 벡터 사용에 익숙해 지는 것이 좋습니다.
<br><br>

### 2.1.1 벡터의 표현
---

  벡터를 가장 간단하게 표현하는 방법은 Python의 list로 표현하는 방법입니다.

  하지만 저희는 Cupy와 Numpy로 이해할 예정이기 때문에 array로 표현할 예정입니다.

  list와 크게 다르지 않기 때문에 코드로 바로 확인해보겠습니다.

```python
numpy_vector = np.array([10, 20, 30])
cupy_vector = cp.array([10, 20, 30])
```

  저희는 앞서 cupy의 기초 파트에서 cupy array의 사용법에 대해서 익혔습니다.
  
  기본적으론, numpy array와 같은 방법으로 사용하시면 됩니다.
  
  다만 cupy의 경우 데이터가 GPU 메모리에 올라갑니다. 
  
  사진으로 확인해보겠습니다.

<amp-img src="{{ site.baseurl }}/assets/images/RAPIDS/Cupy-02/GPU-MEMORY.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<br><br>

### 2.1.2 벡터의 덧셈
---

  벡터의 덧셈에 대해 알아보겠습니다.

  벡터끼리 더한다는 것은, 각 벡터상에서 같은 위치에 있는 성분끼리 더한다는 의미입니다.

<amp-img src="{{ site.baseurl }}/assets/images/RAPIDS/Cupy-02/Vector-add.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<br>

  Numpy와 Cupy 모두 add라는 함수로 구현되어 있습니다.

  그림으로 보았던 예시를 코드로 실험해보겠습니다.

  __Numpy__
```python
vector1 = np.array([1,2])
vector2 = np.array([2,1])

result = np.add(vector1, vector2)
print(result)
```
  __Cupy__
```python
vector1 = cp.array([1,2])
vector2 = cp.array([2,1])

result = cp.add(vector1, vector2)
print(result)
```
<br><br>

### 2.1.3 벡터의 뺄셈
---

  벡터의 뺄셈도 덧셈과 마찬가지로 성분별로 진행합니다.

  Numpy와 Cupy 모두 subtract라는 함수로 구현되어 있습니다.

  __Numpy__
```python
vector1 = np.array([1,2])
vector2 = np.array([2,1])

result = np.subtract(vector1, vector2)
print(result)
```
  __Cupy__
```python
vector1 = cp.array([1,2])
vector2 = cp.array([2,1])

result = cp.subtract(vector1, vector2)
print(result)
```
<br><br>

### 2.1.4 벡터와 스칼라곱
---

  벡터와 스칼라곱은 벡터의 각 원소에 스칼라를 곱하는 것으로 표현합니다.

  이는 multiply 함수로 표현할 수 있습니다.

  __Numpy__
```python
vector = np.array([1,2])
scalar = 2

result = np.multiply(vector,  scalar)
print(result)
```
  __Cupy__
```python
vector = cp.array([1,2])
scalar = 2

result = cp.multiply(vector, scalar)
print(result)
```
<br><br>

### 2.1.5 벡터의 내적
---

  백터의 내적은 각 요소별로 곱한 후 더한 값을 의미합니다.

  numpy와 cupy에선 dot이라는 함수로 구현되어 있습니다.

  __Numpy__
```python
vector1 = np.array([1,2])
vector2 = np.array([2,1])

result = np.dot(vector1, vector2)
print(result)
```
  __Cupy__
```python
vector1 = cp.array([1,2])
vector2 = cp.array([2,1])

result = cp.dot(vector1, vector2)
print(result)
```
<br><br>

### 2.1.6 벡터의 요소별 제곱
---

  벡터의 요소별 제곱은 square라는 함수로 구현되어 있습니다.

  __Numpy__
```python
vector = np.array([1,2])

result = np.square(vector)
print(result)
```
  __Cupy__
```python
vector = cp.array([1,2])

result = cp.square(vector)
print(result)
```
<br><br>


### 2.1.7 벡터의 요소별 루트
---

  벡터의 요소별 루트는 sqrt라는 함수로 구현되어 있습니다.

  __Numpy__
```python
vector = np.array([1,2])

result = np.sqrt(vector)
print(result)
```
  __Cupy__
```python
vector = cp.array([1,2])

result = cp.sqrt(vector)
print(result)
```
<br><br>

### 2.1.8 벡터의 거리
---

  이제 앞서 배운 개념들을 이용해 간단하게 벡터간 거리 연산을 진행할 수 있습니다.

  거리에도 여러가지 개념이 존재하지만, 지금은 가장 일반적이라고 할 수 있는 유클리디언 거리를 측정해보도록 하겠습니다.

  __Numpy__
```python
vector1 = np.array([1,2])
vector2 = np.array([2,3])

sub = np.subtract(vector1, vector2)
square = np.square(sub)
sums = np.sum(square)
result = np.sqrt(sums)
print(result)
```
  __Cupy__
```python
vector1 = cp.array([1,2])
vector2 = cp.array([2,3])

sub = cp.subtract(vector1, vector2)
square=  cp.square(sub)
dot = cp.dot(square, square)
result = cp.sqrt(dot)
print(result)
```
<br><br>

### 2.1.9 벡터의 거리에 대한 다양한 표현
---

  그런데, 위의 표현은 뭔가 간결해보이지 않습니다.

  실은 같은 코드여도 여러가지 방식으로 표현할 수 있습니다.

  지금부터 좀 더 간결해지기 위해 여러가지로 코드를 바꿔 보겠습니다.

  당장 cupy를 사용하지 못하는 분들을 기준으로 하기 위해 numpy코드를 기준으로 해보겠습니다.

```python
vector1 = np.array([1,2])
vector2 = np.array([2,3])

result = np.sqrt(np.sum(np.square(np.subtract(vector1, vector2))))

print(result)
```
<br>
  
  같은 코드인데, 한줄로 표현 가능합니다.

  뭐가 막 많아 보이지는 않지만 한 줄로 표현되어 있기에, 더 복잡해 보이기도 합니다.

  이를 해결하기 위해 square sum부분을 dot으로 바꿔보겠습니다.

```python
vector1 = np.array([1,2])
vector2 = np.array([2,3])

result = np.sqrt(np.dot(np.subtract(vector1, vector2), np.subtract(vector1, vector2)))
print(result)
```
<br>

  조금 나아진 것 같기도한데, 같은 코드를 두번 실행 시켜야하는 점이 걸립니다.

  또한, 그 부분 때문에 더 복잡해 보이기도 합니다.

  따라서 이부분은 나눠서 표현하겠습니다.

```python
vector1 = np.array([1,2])
vector2 = np.array([2,3])


sub = np.subtract(vector1, vector2)
result = np.sqrt(np.dot(sub, sub))
print(result)
```
<br>
  
  조금 더 나아졌지만, 여전히 sub가 두번 들어가는 것이 뭔가 마음에 들지 않습니다.

  이를 함수로 표현하면 좀 더 나아질 수도 있습니다.

```python
def sum_of_square(v):
    return np.dot(v, v)

def distance(v,w):
    return np.sqrt(sum_of_square(np.subtract(v,w)))

vector1 = np.array([1,2])
vector2 = np.array([2,3])

result = distance(vector1, vector2)
print(result)
```
<br>

  어떤가요? 조금 간결해졌나요?

  이 방법 외에도 다양하게 표현할 수 있지만, 우선은 이정도로 넘어가도록 하겠습니다.

  여러분들도 다양한 방법으로 거리를 표현해보시길 바라겠습니다.
<br><br>

## 2.2 행렬
---
<br>

### 2.2.0 행렬의 개념
---
  
  행렬은 보통 2차원 이상의 차원으로 구성되어 있는 숫자의 집합을 의미합니다.

  차원에 따라 2차원 행렬, 3차원 행렬, 다차원 행렬등으로 말하기도 합니다.

  행렬은 보통 list의 list등으로 표현합니다.

  즉, 2차원 list, 3차원 list등으로 작성함으로 표현할 수 있습니다.

  당연하겠지만, numpy와 cupy에선 array를 활용하여 표현할 수도 있습니다.
<br><br>

### 2.2.1 행렬의 표현
---
  
  행렬 파트를 공부할 때는 random.rand함수를 사용하도록 하겠습니다.

  random은 행렬의 원소에 random한 실수 값을 주고 싶을 때 사용하는 메소드입니다.

  그 중 rand함수는, 원하는 shape의 랜덤한 array를 생성해줍니다.

  이때 값은 0에서 1사이입니다.

  __Numpy__
```python
A = np.random.rand(2,3)

print(A)
```
  __Cupy__
```python
B = cp.random.rand(2,3)
print(B)
```
<br><br>

### 2.2.2 행렬의 Shape
---

  행렬은 n개의 행과 k개의 열로 구성되어 있습니다.

  이 때, n과 k는 shape라는 함수로 구할 수 있습니다.

  __Numpy__
```python
A = np.random.rand(2,3)

print(A)
```
  또한 numpy ndarray에 내장되어 있는 shape라는 함수를 사용해서도 구할 수 있습니다.

```python
print(A.shape)
```

  __Cupy__
```python
B = cp.random.rand(2,3)
print(B)
```
  cupy에서는 shape함수를 직접 제공하지 않습니다.

  cupy ndarray의 shape를 사용하여 구할 수 있습니다.
<br><br>

### 2.2.3 단위 행렬
---

  기본적으로 단위 행렬이란, 대각선에 해당하는 성분은 1, 나머지는 0에 해당하는 n차 정사각 행렬을 의미합니다.

  numpy와 cupy에서는 eye라는 함수로 제공되어 있습니다.

  이 때, 굳이 정사각 행렬로 선언하지 않아도 관계 없습니다.

  단, 이런 경우 (0,0)지점 부터 대각 성분만 1이고, 나머지는 전부 0입니다.

  __Numpy__
```python
A = np.eye(3,3)

print(A)
```

  __Cupy__
```python
B = cp.eye(3,3)

print(B)
```
<br><br>


### 2.2.4 행렬 덧셈
---
  
  행렬 덧셈은 벡터간의 덧셈과 유사합니다.

  보통 요소별 덧셈을 의미합니다.

  또한 제공되는 함수도 같습니다.

  __Numpy__
```python
A = np.random.rand(2,3)
B = np.random.rand(2,3)

print("A\n",A)
print("B\n",B)

result = np.add(A,B)
print("Result \n",result)
```

  __Cupy__
```python
A = cp.random.rand(2,3)
B = cp.random.rand(2,3)

print("A\n",A)
print("B\n",B)

result = cp.add(A,B)
print("Result \n",result)
```
<br><br>

### 2.2.5 행렬 곱셈
---

  행렬 곱셈은 행렬간 이항 연산을 의미합니다.

  Numpy와 Cupy에서는 matmul이라는 함수로 제공합니다.

  __Numpy__
```python
A = np.random.rand(2,3)
B = np.random.rand(3,2)

print("A\n",A)
print("B\n",B)

result = np.matmul(A,B)
print("Result \n",result)
```

  __Cupy__
```python
A = cp.random.rand(2,3)
B = cp.random.rand(3,2)

print("A\n",A)
print("B\n",B)

result = cp.matmul(A,B)
print("Result \n",result)
```
<br><br>

### 마무리
---
<br>
  
  이것으로 cupy파트는 마치도록 하겠습니다.

  당연하겠지만 모든 부분을 설명하진 않았습니다.

  선형 대수학 부분도, cupy부분도 마찬가지입니다.

  더 배우고 싶으시다면, cupy나 numpy의 공식 document를 참고하시길 바라겠습니다.

  또한 질문 및 이야기는 언제든지 부탁드리겠습니다.

  질문은 제가 활동하고 있는 사이트 Devstu에서 부탁드리겠습니다.

  [질문 하러 가기](https://devstu.co.kr)

  [Numpy Document](https://numpy.org/doc/)

  [Cupy Document](https://docs.cupy.dev/en/stable/)