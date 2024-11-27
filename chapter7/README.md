# Chapter 7. 앙상블 학습과 랜덤 포레스트
## 앙상블 학습
앙상블 학습이란 일련의 예측기로부터 예측을 수집하여 더 좋은 예측을 얻는 학습 방식. 여러 모델을 학습시켜 정교한 결과를 얻음
## 7.1 투표 기반 분류기
투표 기반 분류기는 각 분류기의 예측을 집계하여 가장 많은 표를 얻은 클래스를 앙상블의 예측으로 하는 분류입니다.  
단순히 다수결을 통해 예측을 결정하는 분류기를 직접 분류기라고 합니다.
랜덤 선택기보다 아주 조금 나은 약한 분류기일지라도 매우 많은 분류기가 모여 앙상블을 이루면 정확도가 높은 분류기가 될 수 있습니다.  
그러나 모든 분류기는 독립적이지 않고 데이터셋의 일부, 혹은 전체를 공유하기 때문에 이론 상의 성능보다 성능 하락이 이루어집니다.  
모든 분류기가 각 클래스별 확률을 제공할 수 있다면 그 확률의 평균을 구하는 것으로 앙상블을 예측을 수행할 수 있습니다. 이를 간접 투표라고 합니다.
## 7.2 배깅과 페이스팅
다양한 분류기를 만드는 방법으로는 서로 다른 훈련 알고리즘을 사용하는 것이 있습니다.
그러나 같은 알고리즘을 사용하더라도 훈련 세트의 서브셋을 랜덤으로 구성하여 분류기를 각각 다르게 훈련시켜 다양한 분류기를 만들 수 있습니다.
- 배깅: 훈련 세트에서 중복을 허용하여 샘플링하는 방식
- 페이스팅: 훈련 세트에서 중복을 허용하지 않고 샘플링하는 방식
일반적으로 배깅과 페이스팅을 이용한 앙상블은 원본 데이터셋으로 하나의 분류기와 비교해 편향은 비슷하지만 분산은 줄어듭니다.
또한 각 분류기는 다른 CPU 코어에서 병렬 학습을 시킬 수 있어 인기가 높습니다.
### 7.2.2 OOB 평가
배깅 방식에서는 샘플링에 중복을 허용하기 때문에 전혀 선택되지 않는 데이터가 생기는데 이를 OOB (Out Of Bag) 방식이라고 합니다. 이 OOB 세트를 이용하여 test set을 따로 분리하지 않고 OOB로 대신해 분류기를 평가할 수 있습니다.  
앙상블의 평가는 각 예측기의 OOB 평가를 평균하여 얻을 수 있습니다.
## 7.3 랜덤 패치, 랜덤 서브스페이스
- 랜덤 패치: 훈련 특성과 샘플을 모두 샘플링
- 랜덤 서브스페이스: 훈련 특성만 샘플링
## 7.4 랜덤 포레스트
배깅을 적용한 결정 트리의 앙상블
- 엑스트라 트리
- 특성 중요도
## 7.5 부스팅
가설 부스팅은 약한 학습기를 여러개 연결해 강한 학습기로 만드는 앙상블 방법
- adaboost
- gradient boosting
  - 축소
- histogram based gradient boosting
## 7.6 스태킹
앙상블의 결과를 취합하는 함수 대신 취합하는 모델을 훈련시켜 사용하는 방법

