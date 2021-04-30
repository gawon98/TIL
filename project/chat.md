# 📌음성 처리

* 구글 Speech-to-Text API (파이썬)

특징 : **동기인식(1분미만) **, 비동기인식(1분이상) , **스트리밍 (마이크 입력)** 기능 지원함 

라이브러리 문서 : https://cloud.google.com/speech-to-text/docs/libraries?hl=ko#client-libraries-install-python



지원하는 Audio 파일 포맷

* WAV

- AIFF
- AIFF-C
- FLAC



* 마이크로 입력된 스트리밍 오디오 텍스트 변환 ?

  https://cloud.google.com/speech-to-text/docs/streaming-recognize?hl=ko



1. 안드로이드 실시간 스트리밍 음성 AWS에서 가져오기 -> 동기인식

2. 스트리밍 인식 (마이크 문제)



# 📌자연어 처리

* 전반적인 텍스트 처리 방법 ( 불용어처리, 형태소 토큰화 , 띄어쓰기처리)

  https://wikidocs.net/21694 

```
from ckonlpy.tag import Twitter
twitter = Twitter()
twitter.morphs('은경이는 사무실로 갔습니다.')
twitter.add_dictionary('은경이', 'Noun') #품사 지정해서 추가
# 빅맥, 맥스파이시 상하이 버거 같은 메뉴 따로 추가해놔야됨
```

* 품사 뽑아내기

  명사 + 수사만 

  

* 키워드 추출 (KR-WordRank 라이브러리)  => 필요없음

  https://soyoung-new-challenge.tistory.com/45

##  데이터 가공

워드 임베딩(Word2Vec)으로 딥러닝 학습데이터 제공

어를 랜덤한 값을 가지는 밀집 벡터로 변환한 뒤에, 인공 신경망의 가중치를 학습하는 것과 같은 방식으로 단어 벡터를 학습

<img src="http://aidev.co.kr/files/attach/images/2997/187/003/1edd311ac54e18660d9afe7e4458dec4.png" alt="dense.png" style="zoom: 33%;" />



# 📌챗봇

* tensorflow 활용

  https://jfun.tistory.com/199 LSTM, Char-CNN

  https://github.com/elymas/ai_chatbot_class/tree/master/07_chatbot_class (텔레그램 활용이라 entity 분석만 참고)

  https://github.com/deepseasw/seq2seq_chatbot (Seq2Seq)



* stt + **Dialogflow** 사용 (구글 챗봇 API) 

  : 한글 자연어 처리 지원 / ai랑 빅데이터가 할게 없어져서 못쓸듯

  https://github.com/allieus/demo-20180805-startup-dev - Google Dialogflow와 파이썬/장고를 활용한 챗봇 만들기

  https://github.com/deepseasw/dialogflow_kakaotalk_chatbot - Dialogflow로 카카오톡 챗봇 만들기

  https://codevkr.tistory.com/74 

  https://github.com/tksrl0379/OutOfKiosk (시각장애인 키오스크)

  

  그 외 챗봇빌더는 제외 (호환성 문제)



## 챗봇에 활용되는 딥러닝 기술

+ **Seq2Seq**: 문장을 그대로 입력받아서 바로 문장이 출력되는 방식 RNN 인코더+디코더 2개 사용 , 단순 잡담에만 사용됨

+ **Char-CNN** : 문장 벡터로 변환하고 특징 추출 후 의도 분류가능 

  ​	참고문서 http://docs.likejazz.com/cnn-text-classification-tf/

* **RNN으로 개체명** 인식  : NER(Named Entity Recognition, 개체명 인식) Bi-LSTM이 좋은 성능을 보인다

<img src="http://aidev.co.kr/files/attach/images/2997/187/003/04365245de80acd53a44f859c28718a8.jpg" alt="python-tensorflow-ai-chatbot-38-1024.jpg" style="zoom: 67%;" />

 위처럼 문장이 입력으로 들어오면 개체명이 출력으로 나온다. 

​	BILSTM 챗봇 코드 : https://github.com/pankaj1131/ChatBot_BiLSTM



# 📌시각화

정확도? 빈도? 

쓴다면 워드임베딩 벡터의 시각화 : 단어간의 유사성을 확인할 수 있음

<img src="https://wikidocs.net/images/page/50704/man.PNG" alt="img" style="zoom: 67%;" />





# 데이터

* ai hub 한국어 대화 ai 데이터

  https://aihub.or.kr/aidata/85

* 대화형 챗봇 데이터

  https://velog.io/@nawnoes/%EC%B1%97%EB%B4%87-QA-%EB%8D%B0%EC%9D%B4%ED%84%B0

* 한국어 말뭉치 목록

  https://github.com/ko-nlp/Korpora

  

음식 주문은 context, intent가 거의 정해져 있음 (~ 주세요 )

중요한건 서버에 저장하는 Entity (메뉴, 수량) 











