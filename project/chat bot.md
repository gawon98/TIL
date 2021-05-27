# ⅠChat Bot 💬

## 0. 챗봇이란❔

: 몇 가지 규칙 또는 인공지능을 기반으로 한 대화형 인터페이스 서비스

 챗봇은 사람이 사전에 입력한 규칙에 의해서만 대화를 할 수 있는 "닫힌 구조"형과 머신러닝을 통해 챗봇 알고리즘이 규칙을 만들어 대화에 탄력적으로 반응하는 "열린 구조"형으로 구분됩니다.

대표적인 닫힌 구조의 챗봇은 식당예약봇, 날씨 봇이 이에 해당되며 

열린 구조는 심심이 등으로 잡담을 수행하는 챗봇이 있습니다.

<img src="https://i2.wp.com/s3-ap-northeast-2.amazonaws.com/contenta-web/froala%2Fuploads%2F1600094843505-1600094843505.png?w=600&ssl=1" alt="img" style="zoom:67%;" />



## 1. 챗봇 전처리 과정

현대 챗봇의 핵심 기술은 자연어 처리(NLP)입니다. 

텍스트 전처리는 용도에 맞게 텍스트를 사전에 처리하는 작업

### 1.1 형태소분석 

자연어 처리에서 말하는 형태소 분석이란 어떤 대상 어절을 최소의 의미 단위인 '형태소'로 분석하는 것을 의미

* 형태소란 의미를 가지는 최소 단위로 정의된다.

 특히 **KoNLPy**(https://konlpy-ko.readthedocs.io/ko/v0.4.3/)는 시중에 공개된 꼬꼬마, 코모란, 트위터, 한나눔, 은전한닢 다섯개 형태소 분석기를 한꺼번에 묶어서 편리하게 사용할 수 있도록 한 패키지이다.



* 코퍼스 (말뭉치)

한글 말뭉치는 한글 어휘와 어휘 특성의 저장소

코퍼스(corpus)는 실제 사람들이 발화된 말이나 발간된 글을 모아놓은 방대한 데이터베이스



### 1.2 단어 임베딩 (Word2Vec)

컴퓨터에게 ‘사과🍎’와 ‘초콜릿🍫’ 이라는 두 단어를 보여준다고 컴퓨터가 두 단어의 개념적인 차이를 이해할 수 있을까요? 

컴퓨터는 단순히 두 단어를 유니코드의 집합으로만 생각할 것이다.



 따라서 단어간의 의미차이를 구분하기 위해 단어 임베딩(word embedding) 알고리즘 중 하나인 Word2Vec를 사용한다.

Word2Vec는 이름 그대로 단어(Word)를 벡터(Vector)로 바꿔주는 방법

파이썬에서는 gensim이라는 패키지에 Word2Vec라는 클래스로 구현되어 있다.



#### 1.2.1 CBOW

① CBOW(Continuous Bag of Words)

② Skip-Gram 

Word2Vec에는 위의 두 가지 방식이 있다. 



CBOW는 주변에 있는 단어들을 가지고, 중간에 있는 단어들을 예측하는 방법  반대로, Skip-Gram은 중간에 있는 단어로 주변 단어들을 예측하는 방법



```
예문
"The fat cat *sat* on the mat"
```

{"The", "fat", "cat", "on", "the", "mat"}으로부터 가운데 단어 sat을 예측하는 것은 CBOW

 이 때 예측해야하는 단어 sat을 중심 단어(center word)라고 하고, 예측에 사용되는 단어들을 주변 단어(context word)라고 함



중심 단어를 예측하기 위해서 앞, 뒤로 몇 개의 단어를 볼지를 결정했다면 이 범위를 윈도우(window)라고 한다.

![img](https://wikidocs.net/images/page/22660/%EB%8B%A8%EC%96%B4.PNG)

윈도우 크기 n =2 일때 윈도우를 옮겨가며 학습을 위한 데이터 셋을 만들어가는 슬라이딩 윈도우 (sliding window)





* CBOW 인공 신경망 도식화

![img](https://wikidocs.net/images/page/22660/word2vec_renew_1.PNG)



Word2Vec은 입력층과 출력층 사이의 충분히 쌓인 은닉층(hidden Layer)이 없으므로 딥러닝 모델이 아님

이렇게 은닉층이 하나일때 얕은신경망(Shallow Neural Network)이라고 부릅니다.

또한 Word2Vec의 은닉층은 일반적인 은닉층과는 달리 활성화 함수가 존재하지 않으며 연산을 담당하는 층을 투사층(projection layer)이라고 부르기도 합니다.



#### 1.2.2 Skip-Gram

Skip-gram은 중심 단어에서 주변 단어를 예측합니다. 

앞서 언급한 예문에 대해서 동일하게 윈도우 크기가 2일 때, 데이터셋

![img](https://wikidocs.net/images/page/22660/skipgram_dataset.PNG)

* Skip-Gram 인공 신경망 도식화

![img](https://wikidocs.net/images/page/22660/word2vec_renew_6.PNG)

성능 비교를 진행했을 때, 전반적으로 Skip-gram이 CBOW보다 성능이 좋다고 알려져 있다



### 1.3 개체명 인식 (NER : Named Entity Recognition)

자연어 처리에서 미리 정의해 둔 사람, 회사, 장소, 시간, 단위 등에 해당하는 단어(개체명)를 문서에서 인식하여 추출 분류하는 기법.

* 예) 철수[인명]는 서울역[지명]에서 영희[인명]와 10시[시간]에 만나기로 약속하였다.

  

1) 룰 기반 NER 접근법

* 룰 템플릿 수동 구성
* 식별된 룰은 특정 dataset에서만 유효



2) 사전기반 NER 접근법

* 정확한 검색에 적합하나, 사전에 정의되지 않은 entity를 놓치기 쉬움
  * fuzzy dictionary matching
  * postprocessing

* 사전을 수동으로 구성해야 함

* ID 정보 제공 가능



3) **기계학습 NER 접근법**

* 알고리즘과 feature가 성능에 큰 영향을 미침

* dataset을 트레이닝하는 표준 주석 필요

* HMM (Hidden Markov Model), SVM (Support Vector Machine), CRF (Conditional Random Field), ME (Maximum Entropy)

  

## 2. 챗봇 알고리즘

### 2.1 RNN (Recurrent Neural Networks)

: 입력과 출력을 시퀀스 단위로 처리하는 모델



* RNN은 은닉층의 노드에서 활성화 함수를 통해 나온 결과값을 출력층 방향으로도 보내면서, 다시 은닉층 노드의 다음 계산의 입력으로 보낸다.

  <img src="https://wikidocs.net/images/page/22886/rnn_image1_ver2.PNG" alt="img"  />

  

* RNN에서 은닉층에서 활성화 함수를 통해 결과를 내보내는 역할을 하는 노드를 셀(cell)이라고 한다.

* 셀(cell) 은 이전의 값을 기억하려고 하는 일종의 메모리 역할  

  => 이를 **메모리 셀** 또는 **RNN 셀**이라고 표현

* 이전 출력이 다음번 출력에 영향을 줌. 그래서 시계열 데이터나 자연어 같이 연속적인 상관관계가 있는 분야에서 많이 사용된다.



단점

* 입력 데이터 사이의 거리가 멀어질 수록 의미를 기억하지 못한다.



### 2.2 LSTM (Long Short Term Memory networks)

바닐라 아이스크림🍦이 가장 기본적인 맛인 것처럼 

앞서 배운 RNN을 가장 단순한 형태의 RNN이라 하여 바닐라 RNN이라 한다. 

![img](https://wikidocs.net/images/page/22888/lstm_image1_ver2.PNG)

바닐라 RNN은 뒤로 갈수록 (time step이 길어질수록) 정보가 충분히 전달되지 못하고 정보량이 손실된다. 



예문

```
'모스크바에 여행을 왔는데 건물도 예쁘고 먹을 것도 맛있었어. 그런데 글쎄 직장 상사한테 전화가 왔어. 어디냐고 묻더라구 그래서 나는 말했지. 저 여행왔는데요. 여기 ___''
```

가장 중요한 정보인 모스크바가 앞에 있기 때문에  ___ 를 예측할때 바닐라 RNN이 충분한 기억력을 갖고 있지 못하면 예측에 실패한다.

=> 이를 장기 의존성 문제 (the problem of Long-Term Dependencies) 라 한다.



이런 단점을 보완한 LSTM은 기존의 RNN과 똑같이 체인 구조를 갖고있지만 4개의 layer가 정보를 주고 받도록 설계되어있다.



<img src="https://t1.daumcdn.net/cfile/tistory/999F603E5ACB86A005" alt="The repeating module in an LSTM contains four interacting layers" style="zoom: 30%;" />

<img src="https://t1.daumcdn.net/cfile/tistory/993A93495ACB86A02F" alt="img" style="zoom: 67%;" />

LSTM의 핵심은 cell state인데, 모듈 그림에서 수평으로 그어진 윗 선에 해당한다. Cell state는 컨베이어 벨트와 같아서, 작은 linear interaction만을 적용시키면서 전체 체인을 계속 구동시킨다. 

<img src="https://t1.daumcdn.net/cfile/tistory/99CB87505ACB86A00F" alt="The cell state of LSTM" style="zoom: 40%;" />

<center>[Cell state]	</center>

<img src="https://t1.daumcdn.net/cfile/tistory/99C98C4F5ACB86A01F" alt="A gate of LSTM" style="zoom:70%;" />

STM은 cell state에 뭔가를 더하거나 없앨 수 있는 능력이 있는데, 이 능력은 gate라고 불리는 구조에 의해서 조심스럽게 제어된다.

Gate는 정보가 전달될 수 있는 추가적인 방법으로, sigmoid layer와 pointwise 곱셈으로 이루어져 있다.

Sigmoid layer는 0과 1 사이의 숫자를 내보내는데, 이 값은 각 컴포넌트가 얼마나 정보를 전달해야 하는지에 대한 척도를 나타낸다. 

그 값이 0이라면 "아무 것도 넘기지 말라"가 되고, 값이 1이라면 "모든 것을 넘겨드려라"가 된다.

LSTM은 3개의 gate를 가지고 있고, 이 문들은 cell state를 보호하고 제어한다.



출처: https://dgkim5360.tistory.com/entry/understanding-long-short-term-memory-lstm-kr [개발새발로그]



### 2.3 Seq2Seq

딥러닝으로 챗봇을 구현할때 많이 쓰이는 모델

문장을 그대로 입력 받아서 바로 문장이 출력되도록 하는 방식. Encoder와 Decoder 두개의 RNN을 사용하여 구현합니다. 

<img src="http://aidev.co.kr/files/attach/images/2997/273/002/ccba27bcf9f09f4f867586c77d1d33bb.png" alt="basic_seq2seq.png" style="zoom:40%;" />

그림처럼 ABC가 입력으로 들어오면 WXYZ가 출력으로 나온다.

<go>와 <eos>는 시작과 끝을 나타내는 기호

'ABC'를 Encoder로 순차적으로 넣고 그 다음 Decoder에서 결과를 출력한다. 여기서 Decoder의 출력이 다시 입력으로 들어가는 것을 볼 수 있다.



https://github.com/deepseasw/seq2seq_chatbot

<img src="https://github.com/deepseasw/seq2seq_chatbot/raw/master/image/image03.png" alt="image03.png" style="zoom: 40%;" />

* 문장이 어떤 의미인지 구분하는 분류 모델과 달리, 질문에 맞는 대답 문장을 바로 출력
* 훈련시에는 인코더 입력, 디코더 입력, 디코더 출력의 세 가지 데이터가 필요
* 예측시에는 미리 디코더 입력과 디코더 출력을 만들어놓을 수 없음. 그래서 LSTM을 한 번씩만 수행하여 이전 출력을 다음 번 입력으로 넣으면서 반복한다.



# Ⅱ Kochat 💬

https://pypi.org/project/kochat/

![introduction_kochat](https://warehouse-camo.ingress.cmh1.psfhosted.org/39f4405094cd1054693583dc9da9b56455d139a5/68747470733a2f2f757365722d696d616765732e67697468756275736572636f6e74656e742e636f6d2f33383138333234312f38353935383030302d31623865643038302d623963642d313165612d393964362d3639623437326633653266662e6a7067)

1. 데이터셋 객체 생성
2. 임베딩 프로세서 생성
3. 의도(Intent) 분류기 생성
4. 개체명 인식기 생성
5. 딥러닝 챗봇 RESTful API 학습 & 빌드 (시나리오 기반)
6. View 소스파일 연결
7. 챗봇 어플리케이션 서버 가동



Close domain 챗봇으로 Slot filling 방식으로 구현된다. 

Intent를 분류 한 후 Entity를 인식해 대답을 생성하는 방식 

해당 Intent에 맞는 슬롯이 다 채워질때까지 재질문을 하고, 다 채워지면 NER을 통해 어떤 API를 호출할지 결정한다.  (초기 개발자가 정한 API : 날씨, 맛집, 미세먼지, 여행지)

위의 흐름대로 Intent 분류 모델, Entity 인식 모델, 그리고 대답 생성 모듈 (예제에서는 크롤링)이 필요하다

Kocrawl : https://pypi.org/project/kocrawl/

 Kochat은 이 세가지 모듈과 이를 서빙할 Restful API까지 모두 포함



## 0. 임베딩

* FastText : Word2vec 의 확장판

  Word2Vec는 단어를 쪼개질 수 없는 단위로 생각한다면, FastText는 하나의 단어 안에도 여러 단어들이 존재하는 것으로 간주한다. 즉 내부 단어(subword)를 고려하여 학습한다.

```
#예제

from gensim.models import FastText
model = FastText(result, size=100, window=5, min_count=5, workers=4, sg=1)
model.wv.most_similar("electrofishing")
```

```
[('electrolux', 0.7934642434120178), ('electrolyte', 0.78279709815979), ('electro', 0.779127836227417), ('electric', 0.7753111720085144), ('airbus', 0.7648627758026123), ('fukushima', 0.7612422704696655), ('electrochemical', 0.7611693143844604), ('gastric', 0.7483425140380859), ('electroshock', 0.7477173805236816), ('overfishing', 0.7435552477836609)]
```

FastText는 유사한 단어를 계산해서 출력하고 있음을 볼 수 있다.

* Word2vec 



현재는 위의 두 Gensim모델만 지원한다.



## 1. Intent

* CNN text 분류

텍스트 CNN의 필터는 텍스트의 지역적인 정보, 즉 단어 등장순서/문맥 정보를 보존

kochat에서 1D CNN를 사용해 intent 모델을 형성

<img src="http://i.imgur.com/JN72JHW.png" alt="img" style="zoom:50%;" />

필터의 크기(n) 를조절하며 n개의 단어로 이루어진 문장을 각 단어별로 k차원으로 행벡터에 임베딩 

 참고 : https://ratsgo.github.io/natural%20language%20processing/2017/03/19/CNN/



* BI-LSTM

양방향 LSTM은 두 개의 독립적인 LSTM 아키텍처를 함께 사용하는 구조

![img](https://wikidocs.net/images/page/94748/bilstm1.PNG)

주황색 LSTM 셀은 순차적으로 입력을 받습니다. 양방향 LSTM은 뒤의 문맥까지 고려하기 위해서 문장을 오른쪽에서 반대로 읽는 **역방향의 LSTM 셀**(위 그림에서 초록색)을 함께 사용

 특징 

1. 출력값에 대한 손실을 최소화하는 과정에서 모든 파라미터를 동시에 학습되는 종단간 학습 가능
2. 단어와 구(Phrase)간 유사성을 입력벡터에 내재화하여 성능 개선
3. 데이터 길이가 길어도 성능이 저하되지 않음



## 2. Entity

* BI-LSTM

Entity를 BIOES태깅을 사용하여 라벨링



## 3. Fallback

학습된 intent에 벗어난 말이 들어올때 fallback으로 검출

`DistanceClassifier`의 경우 out distribution 샘플들과 in distribution 샘플들의 Knn을 feature로 하여 머신러닝 모델을 학습

선형 문제로 해석하기 때문에 kochat에서 선형 SVM, 로지스틱 회귀 등을 주로 이용 



추가로 OOD데이터셋 (Out of distribution) 도 라벨링해서 추가하는데 Fallback 검출에서 사용

<img src="chat bot.assets/image-20210526202045150.png" alt="image-20210526202045150" style="zoom: 80%;" />



## 4. Loss

* Intent Loss 함수는 기본적인 CrossEntropyLoss와 다양한 Distance 기반의 Loss함수를 활용 (코사인, 가우스  ...)

* Entity Loss 함수는 기본적인 CrossEntropyLoss와 확률적 모델인 Conditional Random Field (이하 CRF) Loss를 지원

  CRF Loss를 적용하면, EntityRecognizer의 출력 결과를 다시한번 교정하는 효과를 볼 수 있다.

  

# Ⅲ Dialog flow 💬

동작과정 

Dialogflow agent에 사용자가 입력한 text에 대한 의도 파악을 요청한다. 

Dialogflow agent는 학습한 데이터를 토대로 의도에 상응하는 응답을 Google Assistant에 보내 사용자에게 Agent의 반응을 출력해 보여준다

<img src="chat bot.assets/image-20210526205435840.png" alt="image-20210526205435840" style="zoom: 80%;" />



대화의 흐름을 이어가는 3가지 개념

- Intent (의도) 
- Entity (속성)
- Context (문맥) 

<img src="https://miro.medium.com/max/3200/0*sENDk_t4v5j_epXQ" alt="img" style="zoom:40%;" />

이 중 Context 만 살펴보면  ‘내일 오후 2시 되나요’ 에서 무엇을 위한 ‘내일 오후 2시’ 인가를 파악하기 위해서 전체 대화의 문맥을 이해하고

그 전에 대화가 되었던 ‘수리’ 라는 것을 기억하는 것을 의미한다.



## 활용 알고리즘

* 규칙기반 (rule-based matching)

 규칙 기반의 챗봇(Chatbot)은 개발자가 미리 지정한 키워드와 패턴을 통해 사용자의 의도(Intent)를 파악한다.

* ML matching



기본적으로 Dialogflow는 intent 매칭을 할때 두 알고리즘 모두를 사용한다. 

따라서 예문이 적을땐 두 알고리즘을 모두 활용하는 것이 ML only 모드 보다 더 좋은 매칭결과를 얻게된다.







# 그 외 참고

 Yoon Kim, "Convolutional Neural Networks for Sentence Classification" ,  2014

박상현 , "챗봇 프레임워크 성능 향상을 위한 점진적 학습 기법" , 2019

김주은 외 4," Google Dialogflow를 활용한 레시피 챗봇에 관한 연구" ,목포대학교

[고상준, 윤호영, and 신동명. "양방향 LSTM을 활용한 전력수요 데이터 예측 기법 연구" *한국소프트웨어감정평가학회 논문지* 14.1(2018):33-40](http://www.i3.or.kr/html/paper/2018-1/(5)2018-1.pdf)

http://aidev.co.kr/chatbotdeeplearning/7921

http://aidev.co.kr/index.php?&mid=chatbotdeeplearning&search_keyword=lstm&search_target=title_content&document_srl=3187








