---
layout: post
cover: 'assets/RAPIDS/Main.png'
title: 01. RAPIDS Installation
published: true
date: 2020-08-02 22:00:00
tags: [RAPIDS ,Python, Machine Learning,DataScience, Cupy, Cudf,CuML, Data, Data Science]
author: Lee Je Young
---


# 01. RAPIDS Installation
---
  <br><br>
  
  우선 첫번째 챕터 설치부터 살펴보겠습니다.
  
  솔직히 설치 부분은 비교적 간단하기 때문에, 굳이 보시지 않으셔도 상관없습니다.
  
  다만, 설치시에 문제가 있으시던가 하는 것을 방지하기 위하여 그리고 RAPIDS공식 홈페이지에 대해 알려드리기 위하여, 작성하였습니다.
  
 
  <br><br>
  
## Enviroment
---
  <br><br>
  
  제가 사용한 환경은 다음과 같습니다.
  
>Ubuntu >= 18.04 LST
><br>Anaconda
><br>Python >= 3.6.8
><br>RAPIDS(stable) >= 0.12
><br>CUDA >= 10.0
><br>Cudnn >= 7.6
><br>NUMPY >= 1.16.1
  
  <br><br>
  
  여러분들은 각자가 원하는 환경으로 구성하시면 됩니다.
  
  다만, 이 칼럼에서는 저랑 비교적 똑같은 환경을 구축하시는것을 추천드립니다.

  
## RAPIDS
---
  <br><br>
  
  [RAPIDS](https://rapids.ai/)
  
  RAPIDS에 대한 대부분의 자료는 이곳에서 찾아보실 수 있습니다.
  
  제가 작성하는 글은 이 사이트와, BLOG, SLACK, NVIDIA DLI등을 참고하여 작성하였습니다.
  
  <br><br>
  
## Installation
---

  <br><br>
  
  자, 그러면 설치를 시작해 볼까요?
  
  RAPIDS 공식 사이트에 GET STARTED 버튼을 누르면, 설치 방법과, 설치할 수 있는 환경등을 설명해줍니다.
  
  이번 칼럼에서는 아나콘다 환경에서의 설치 방법만 다루고 있습니다. 다른부분에 대해서는 다음 기회에 살펴보도록하겠습니다.
  
  아나콘다에서는 어떻게 설치하는지 그림으로 먼저 살펴보겠습니다.
  
  
<amp-img src="{{ site.baseurl }}assets/RAPIDS/install/RAPIS_install.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  
  순서대로 살펴 볼까요?
  
  우선 가장 위에는 어떤 방법으로 설치할 것인지에 대한 부분입니다.
  
  지금은 콘다환경에서 사용하기 때문에 콘다를 선택했습니다.(실은 제가 도커를 다루줄 잘 모르기때문에, 도커에 대한 부분은 도커 칼럼을 연재하면서 배워두려고합니다.)
  
  그리고 Stable버젼과 Nightly버젼이 존재하는데, 우선 Stable버젼을 사용하도록하겠습니다.
  
  마찬가지로 전 우분투 18.04를 사용하였으나, 실은 16.04와 18.04가 설치시에는 명령어 차이가 존재하지 않습니다.
  
  그 다음은 파이썬 버젼에 대한 문제인데, 제 콘다 버젼은 파이썬 3.7까지 밖에 지원을 하지 않습니다.
  
  그리고, 제가 실은 텐서플로 1버젼을 즐겨 사용했었기에 3.6버젼으로 선택했습니다. 이는 취향의 문제임으로 본인 취향껏 선택하시길 바라겠습니다.
  
  마지막으로 CUDA버젼인데, 제가 사용하고 있는 노트북은 Geforce 1050을 사용하고 있습니다.
  
  따라서 지원 여부를 잘 보고 선택해야하는데, 지금은 그나마 가장 안정화 버젼은 CUDA10.0을 선택했습니다.
  
  (이 부분도, 어차피 콘다를 쓴다면 어떤 버젼을 사용하셔도 상관 없을 것으로 알고 있습니다.)
  
  자 이제 선택이 모두 끝났습니다.
  
  마지막으로 출력된 커맨드를 자신의 컴퓨터에 복사하여 사용하시면 됩니다.
  
  모두 귀찮으실수도 있기에, 제 글에도 제 환경과 동일한 명령어 부분만 작성해 놓겠습니다.
  
  ```bash
  conda install -c rapidsai -c nvidia -c conda-forge \
    -c defaults rapids=0.14 python=3.6 cudatoolkit=10.1
  ```
  
  <br><br>
  
## Installation check
---

  <br><br>
  
  자 이제 마지막으로 성공적으로 설치되었는지 확인해볼까요?
  
  간단한 명령어만 테스트 해보겠습니다.
  
  저는 주피터 환경에서 테스트 하였습니다.
  
  ```python
  import cupy as cp
  import cudf as cd
  import cuml as cm
  ```
  
  ```python  
  X_cp = cp.array([1,2,3,4,5,6,7,8,9])
  y_cp = cp.array([11,22,33,44,53,66,77,87,95])

  print("X : ", X_cp)

  !nvidia-smi
  ```
  
<amp-img src="{{ site.baseurl }}assets/RAPIDS/install/Testing.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  
  마지막으로 원본 코드 주소를 첨부하겠습니다.
  
  [원본코드 보러가기](https://github.com/Ign0reLee/Data_Science_With_RAPIDS/blob/master/Chapter%2001.Installation/Testing_Installation.ipynb)
  
  깃허브에서 보시면 추가로 행렬간의 내적으로 시간을 측정한 부분도 포함되어있습니다.
  
  이번챕터에서는 다루지 않았지만, 시간이 더 빨랐다 정도만 챙겨가시면 될 것 같습니다.
  
  감사합니다! 다음주에 뵙겠습니다.