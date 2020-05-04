---
layout: post
cover: 'assets/images/tree.jpg'
title: Nvidia Deep Learning Institute Review
published: true
date: 2020-05-03 22:00:00
tags: [Nvidia Deep Learning Institute, Review, DLI, Computer Vision, Deep Learning, Machine Learning]
author: Lee Je Young
---
<meta charset="UTF8">
<h1>Nvidia Deep Learning Institute Review<br /></h1>

<br />우연치 않은 기회로 DLI리뷰 스터디들 진행하게되었습니다.

각자 다른 이유로 모인 세명이지만 성실이 리뷰를 진행해 볼까합니다.

처음 진행하는 리뷰이기에 어떻게 진행하는지 잘 몰랐던 것이 가장 힘든 점이었습니다.

저희는 매주 밤 10시에 모여 PPT를 통해 요약, 느낀점, 추천여부등을 발표하는 활동을 진행하고 있습니다.

총 요약본은 그림으로 같이 첨부하도록 하겠습니다.

많이 부족하지만 앞으로도 잘 부탁드리겠습니다.

질문있으시면 언제든지 메일을 보내주세요! 기다리고 있겠습니다.

또한 이런 기회를 만들어주신 Nvidia, 손해인님께 감사드립니다.

<hr />
<center>

<br /><h1>Review</h1>

<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/Review/1.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>

<h2>Index </h2><br />

<h4>-Summary</h4>

<h4>-Experience</h4>

<h4>-Recommendation</h4>

</center>


<hr />
<br />
<center>
<h2>Summary</h2>


<br />
<h4>Welcome</h4>
</center>

<br />Introduction of Deep Learning

<br />Brief the objectives of this course.
<hr />
<br />
<center>
<h4>Training Deep Neural Networks</h4>
</center>

*Biological Inspiration

	-딥러닝은 컴퓨터가 examples(data)로부터 학습하게 만든다.
	
	-이 때, 두가지를 고려해야한다.
	
		1.문제속 패턴이 식별되는가?
		
		2.패턴을 보여줄 만큼 데이터가 충분한가?
		
	-Game 1
	
		+아무런 사전 정보 없이 사진 속에 Louie가 있는지 확신에 대해 0~10사이의 점수를 매긴다.
		
	-Deep Neural Networks : GPU Task1
	
		+영상 : Sweeping across industries
		
			*딥러닝이 산업 어느 분야에서 쓰이는지 살펴본다.
			
			*과거의 전통적인 기계학습과 Deep/End-to-End Learning의 차이
			
				1.기계학습은 Hand designed feature가 제공되지만 Deep Learning은 그렇지 않다.
				
				2.End-to-End의 의미 : 문제 식별을 위한 패턴을 스스로 학습한다.
				
	-DIGITS를 이용한 Image classifier 구현
	
		+사진이 Louie인지 아닌지 판별하는 모델을 만들어본다.
		
		+2 Epochs만 학습했을 경우, 정확도가 50% 이하지만 100 Epochs동안 학습한 후, 정확도가 99%에 이른다.
		
	-영상
	
		+모델의 output과 실제 output을 비교하고 차이를 이용하여 Weights를 갱신한다.
		
	-Big Data : GPU Task 2
	
		+근래 기계학습을 발전시키는데 기여한 요소 세 가지가 있다.
		
			1.Deep Neural Network
			
			2.The GPU
			
			3.Big data
			
		+이 세 가지를 neural network를 학습시키는데 사용해볼 것이다.
		
		+새로운 데이터에 대해 neural network가 잘 작동하도록 학습시키는 것은 환경의 다양성이 표현되는 충분한 데이터가 필요하다.
		
		+영상
		
	-Deploying out Model : GPU Task 3
	
		+개와 고양이 구분하기.
		
	
<br />
<hr />
<center>
<h4> DIGITS Examples</h4>

<br />
<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/Review/Train_Data.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<Digits Data Load>
<br />
<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/Review/Train_model_1.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<Digits Train model 1>
<br />
<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/Review/Train_model_2.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<Digits Train model 1>
<br />

<br /> 
<hr />
<center>
<h4>Performance</h4>
</center>

	-Performance during Training : GPU Task 4
	
		+정확도를 상승시키는 방법에 대해 공부한다.
		
	-Object Detection : GPU Task5
	
		+Using deployment
		
		+Caffe를 이용하여 객체 인식을 학습해보자.
		
		+의의 : Deep Learning과 전통 프로그래밍을 합쳐 이전의 불가능한 문제들에 대해 높은 성능을 보여줌을 설명한다.
		
<br />
<hr />
<center>
<h4> Assessment</h4>
</center>
	
	-Train and deploy a deep neural network.
	
		+고래의 머리가 그려져 있는 사진과, 그렇지 않은 사진들로 이루어진 데이터셋을 학습시켜라. 
		
		+DIGITS와 Caffe(Python) 사용법을 테스트한다.
		
		+Model과 Weights, Dataset 경로 설정 관련 빈칸 문제가 나온다.
		
		+최종적으로 모델을 학습시키는 메서드의 사용법을 숙지 해야 한다.
		

<br />
<hr />
<center> 
<h2>Experience</h2>
</center>

<hr />
<br />
<center>
<h4>Experience-구정수</h4>
</center>

<br /><br />기본적으로 영어에 대한 거부감이 없으며, 영어로 된 교육자료를 읽고 이해할 수 있는 능력이 필요하다.
<br /><br />Deep Learning의 기초 알고리즘에 대해 밑바닥부터 자세하게 알려주진 않는다. 
<br /><br />딥러닝의 커다란 개념들을 설명한다.
<br /><br />학습 과정을 DIGITS 프레임워크를 통해 이해하기 쉽게 시각화하여 볼 수 있다.
<br /><br />쉽게 적용 가능하고 성능이 좋은 딥러닝 모델과 데이터셋이 준비되어있다. 
<br /><br />DIGITS를 사용하여 공부하는 것은 장점과 단점 모두 가지고 있다.
<br /><br />장점은 어렵지 않게 학습 과정을 살펴볼 수 있다는 것이고
<br /><br />단점은 학습에 사용되는 알고리즘을 공부할 수 없다는 것이다.
<hr />
<br />
<center> 
<h4>Experience-이제영</h4>
</center>
<br /><br />Digits을 사용함으로써 모델이 더 간단 해졌다.
<br /><br />기본이 caffe에서 추가된 부분인 것 같던데, 다루기 힘든 부분을 다루기 쉽도록 잘 도와준 것 같다.
<br /><br />그냥 내용에서 직접 하는 부분이 proto 부분등 이므로 조금 부족한 것 같기도 하다.
<br /><br />처음 배우는 사람이라면 굉장히 알차고 눈에 보이는 성과를 금방 낼 수 있을 것 같아 즐거울 것 같다.
<hr />
<br />
<center> 
<h4>Experience-박경훈</h4>
</center>
<br /><br />강의를 시작하게 되면 어떤 순서대로 강의를 진행하는지 한눈에 알 수 있다. 
<br /><br />그 강의 시간도 표기가 되어있기 때문에 시간관리에 용이했다. 
<br /><br />중간에 강의를 그만두어도 진행한 부분으로 바로 이동하여 편리했다. 
<br /><br />강의 내용은 글, 동영상, 퀴즈, 실습 으로 구성 되어있다.  내용은 굉장히 이해하기 쉽게 설명 되어있고, 실습과 퀴즈를 통해  빠르게 이해할 수 있었다.
<br /><br />실습은 NVIDIA에서 제공하는 서버를 이용하기 때문에 컴퓨터에 대한 걱정은 하지 않았다.
<br /><br />실습을 진행하는 방법을 잘 강의해주기 때문에 진행하는데 있어서 문제는 없었다. 제공 받은 데이터를 이용해 직접 모델을 만들 수 있고, 그 모델을 바로 테스트 해볼 수 있기 때문에 굉장히 재미 있었다.


<br />
<hr />
<center> 
<h2>Recommendation</h2>
</center>
<hr />

<br />
<center> 
<h4>Experience-구정수</h4>
</center>
<br /><br />시간이 여유롭고 영어와 친해지고 싶다, 혹은 영어에 부담 없는 사람들에겐 추천할 만 하다.
<br /><br />딥러닝의 큰 범주의 개념들과 흐름을 파악할 수 있었다. 
<br /><br />영어에 거부감이 있거나, 공부할 시간이 얼마 없는 사람, 그리고 딥러닝의 알고리즘부터 차근차근 공부하고 싶은 사람들에겐 추천하지 않는다.
<hr />
<br />
<center> 
<h4>Experience-이제영</h4>
</center>
<br /><br />처음 딥러닝을 접하는 사람에게는 추천
<br /><br />컴퓨터 비전 기초 부분을 이해하고 싶으면 추천
<br /><br />코딩은 약하지만 인공지능은 해보고 싶다면 추천
<br /><br />DIGITS에 관심 있는 사람들에게는 추천
<br /><br />Caffe를 깊게 배워 보고 싶으면 비 추천
<br /><br />파이썬 코드를 깊게 다루면서 인공지능을 배우고 싶으면 비추천
<hr />
<br />
<center> 
<h4>Experience-박경훈</h4>
</center>
<br /><br />모든 글과 강의가 영어로 되어있기 때문에 이해하기 어려울 수 있다.
<br /><br />프로그래밍을 경험해본 사람이라면 강의내용 그대로 진행하여도 이해할 수 있어 쉽다.
<br /><br />
<hr />
<br />
<center>
<h2>인증서</h2>
</center>

<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/In/Fundamentals_of_DL_for_Computer_Vision_institute_구정수.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<br />
<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/In/Fundamentals_of_DL_for_Computer_Vision_institute_박경훈.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<br />
<amp-img src="{{ site.baseurl }}assets/DLI_Computer_Vision/In/Fundamentals_of_DL_for_Computer_Vision_institute_이제영.png" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>

<br />
<hr />

긴 글 읽어주셔서 감사합니다!

모든 리뷰는 주관적이라는점 알아주시면 감사하겠습니다!

앞으로 저희의 리뷰를 통해 Nvidia에서 열리는 DLI 프로그램에 대해 궁금하신점을 해결해가셨으면 좋겠습니다!

지금 리뷰는 내용 요약이 들어가있지만, 실제로 DLI프로그램을 진행하면 직접 코딩하시면서 하실 수 있습니다.

이런 흐름이다~ 라고 생각하시고 보시면 좋을 것 같습니다 ㅎㅎ 감사합니다!

다음주에는 CUDA C/C++리뷰로 돌아오겠습니다!