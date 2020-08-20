---
layout: post
cover: 'assets/RAPIDS/Main.png'
title: 00. Data Science With RAPIDS Introduction
published: true
date: 2020-08-02 19:00:00
tags: [RAPIDS ,Python, Machine Learning,DataScience, Cupy, Cudf,CuML, Data, Data Science]
author: Lee Je Young
---

# 00. Data Science With RAPIDS Introduction
---
  <br><br>
  안녕하세요, 그리고 오랜만입니다.
  
  기나긴 준비 시간이 끝나고, 드디어 새로운 칼럼을 연재하고자합니다.
  
  과거 DLI Review를 진행하다가 RAPIDS와 처음 만났습니다.
  
  그리고 RAPIDS는 제게 굉장히 큰 충격을 안겨주었습니다.
  
  기존의 NUMPY와 PANDAS를 GPU에서 돌릴 수 있다.
  
  매서드가 동일하여 이름만 바꾸면 된다.
  
  이런 이야기들을 처음 그대로 들었을때는 별거 아니다 싶다가도 실제로 돌려보니 굉장히 개선되는 점이 많았습니다.
  
  아직 RAPIDS는 우리나라에 제대로 소개하는 글이 없어서 아쉬웠습니다.
  
  그래서 이번기회에 한글로 소개하고자합니다.
  
  아직 학부생이기에 부족한 점도 많고, 제가 모르는 점도 많을 것 같습니다.
  
  다만, GPU를 이용한 데이터 과학에 대해서 한번 생각해보시는 계기가 되셨으면합니다.
  
 
  <br><br>
## Enviroment
---
  <br><br>
  아쉽지만, 이 칼럼에서는 환경을 조금 제한해야합니다.
  
  공식적으로 지원되고 있는 환경이 넓지는 않습니다.
  
  왠만하면 아래 환경을 따라가시기를 권장드립니다.
  
  또한 리눅스를 사용하기 어려우신 분들은 콜랩환경을 권장드립니다.
  
  다만, 콜랩 환경은 세션을 실행시킬 때 마다, RAPIDS를 새로 인스톨 해주어야합니다. 
  
  이와 관련해서는 다시 글을 작성하도록 하겠습니다. 
  
  Anaconda사용을 권장드립니다.
  
  마지막으로 Ubuntu환경을 작성하기로는 18.04LST 이상이라고 적혀있으나, 제가 사용하는 버전 이상이라는 의미입니다.
  
  또한, 하위 버전에서도 아마 가능할겁니다. 제가 아직 리눅스를 잘 다루지 못하여, 테스트를 할 수 없는점 죄송합니다.
  
  
>Ubuntu >= 18.04 LST
><br>Anaconda
><br>Python >= 3.6.8
><br>RAPIDS(stable) >= 0.12
><br>CUDA >= 10.0
><br>Cudnn >= 7.6
><br>NUMPY >= 1.16.1
  
  <br><br>

  
## Goal Of This Column
---
  <br><br>
  이 칼럼의 목표에 대해 알려드리겠습니다.
  
  우선 RAPIDS는 다음과 같이 구성되어 있습니다.
  
<amp-img src="{{ site.baseurl }}assets/RAPIDS/intro/RAPIDS_all.jpg" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  
  이번 칼럼은 Data Science의 기초부분을 다루고자합니다.
  
  따라서 딥러닝 부분에 대한 이야기는 나중에 따로 칼럼을 준비하겠습니다.
  
  이 칼럼에서 알아보고자 하는 부분은 Numpy를 대체할 수 있는 Cupy,그리고 PANDAS를 대체할 수 있는 Cudf 마지막으로 scikit-learn을 대체할 수 있는 cuML부분입니다.
  
  또한 각각의 예시를 CPU버젼, GPU버젼으로 시간을 비교하며 진행하도록 하겠습니다.
  
<amp-img src="{{ site.baseurl }}assets/RAPIDS/intro/RAPIDS_all_now.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
  <br><br>
  
---

  <br><br>
  앞으로 일주일에 한번 연재하는 것이 목표입니다.
  
  앞으로도 잘 부탁드리겠습니다. 감사합니다!

  질문 및 이야기는 언제든지 부탁드리겠습니다.

  질문은 제가 활동하고 있는 사이트 Devstu에서 부탁드리겠습니다.

  [질문 하러 가기](https://devstu.co.kr)