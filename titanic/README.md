Titanic Survival Analysis & Prediction
📌 프로젝트 개요

이 프로젝트는 Kaggle Titanic 데이터를 활용해 탑승객의 생존 여부(Survived) 를 분석하고 예측하는 것을 목표로 합니다.
데이터 확인 → 전처리 → 탐색적 분석(EDA) → 파생변수 생성 → 로지스틱 회귀 모델링 과정을 거쳤습니다.

📂 데이터 설명

PassengerId: 승객 고유 번호

Pclass: 객실 등급 (1, 2, 3)

Sex: 성별 (m, f)

Age: 나이

SibSp: 형제/배우자 수

Parch: 부모/자녀 수

Fare: 운임 요금

Embarked: 탑승 항구 (C, Q, S)

Survived: 생존 여부 (0 = 사망, 1 = 생존)

추가 파생 변수:

Family = SibSp + Parch (가족 수)

IsAlone = (Family == 0) (혼자 여부)

🔎 분석 과정
1. 데이터 전처리

Embarked 결측치를 최빈값 S로 채움

Sex, Embarked를 숫자/문자 값으로 변환

2. 데이터 탐색 (EDA)

나이(Age), 요금(Fare) 분포: 저연령층, 낮은 요금대 승객이 많음

객실 등급(Pclass)별 생존률: 1등석 생존률 ↑, 3등석 생존률 ↓

성별(Sex)별 생존률: 여성 생존률이 남성보다 월등히 높음

탑승항구(Embarked)별 생존률: C항구에서 탑승한 승객의 생존률이 가장 높음

가족 수(Family): 가족이 3명일 때 생존률이 가장 높음(95% 이상), 7명·10명은 모두 사망

3. 상관계수 분석

Survived와 가장 높은 상관: 성별(Sex, 0.40)

다음으로 영향 있는 변수: 운임(Fare, 0.17), 객실 등급(Pclass, -0.24)

4. 로지스틱 회귀 모델

입력 변수: Pclass, Sex, Age, Fare, Family

출력 변수: Survived

학습/테스트 데이터 분리 (80:20)

LogisticRegression(max_iter=1000) 적용

📈 결과

정확도(Accuracy): 약 76%

혼동 행렬

실제 사망자(0): 189명 중 175명 맞춤 (Recall = 93%)

실제 생존자(1): 73명 중 25명만 맞춤 (Recall = 34%)

➡️ 즉, 사망자는 잘 맞추지만 생존자는 많이 놓친다는 결과.

💡 인사이트

여성, 1등석, 요금이 높을수록 생존 확률이 높다.

가족이 3명일 때 생존률 최고, 대가족은 생존률 낮음.

로지스틱 회귀는 기본 정확도는 괜찮지만, 생존자 예측 성능(Recall)이 낮다.

🚀 향후 개선 방향

모델 다양화: RandomForest, XGBoost, LightGBM 적용

평가지표 확장: ROC Curve, AUC, Precision-Recall Curve 확인

Threshold 조정: 생존자 Recall을 높이는 방향으로 기준값 변경
