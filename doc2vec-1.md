---
description: 2022/10/07
---

# Doc2vec 이론

● 모델 코드

model = g.Doc2Vec(docs, vector_size=vectorsize, window_\_size=window\_size, min\_count=min\_count, sample=sampling\_threshold, workers=worker\_count, hs=0, dm=dm, negative=negative\_size, dm\_concat=0)



● 학습 과정 코드

1. Doc2Vec 클래스 init에서 super()를 통해 Word2Vec 클래스 호출
2. Word2Vec 클래스 init에서 코퍼스 정상 체크 함수 \_check\_corpus\_sanity(), 단어 사전 생성 함수 build\_vocab(), 훈련 함수 train() 실행
3. Word2vec 클래스의 train() 내에 싱글 에포크 훈련 함수 \_train\_epoch() 실행
4. Word2vec 클래스의 \_train\_epoch() 내에 여러 개의 배치에 대하여 반복 수행 함수 \_worker\_loop() 실행
5. Word2vec 클래스의 \_worker\_loop() 내에 하나의 배치에 대한 훈련 함수\_do\_train\_job() 실행
6. Doc2vec 클래스에서 \_do\_train\_job() 함수를 오버라이딩&#x20;
7. \_do\_train\_job() 함수에서 dbow, pvdm (sum or average), pvdm (concat) 중에 설정해둔 훈련 방법으로 훈련 진행 (doc2vec\_inner.cpp, doc2vec\_iner.pyx, doc2vec\_inner.pxd를 통한 내부 함수 실행) \*cpp = 함수 구현, pyx = 파이썬 문법을 기반으로 C/C++ 루틴 호출을 위한 cython언어(cython to c/c++), pxd = c/c++ 헤더와 동일한 cython 스크립트

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

