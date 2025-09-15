1. 프로젝트 개요

주제: Kaggle 신용카드 데이터를 활용한 고객 세분화 분석
목표: K-Means 군집분석을 통해 고객을 유형별로 분류하고, 각 군집의 소비 성향을 기반으로 맞춤형 마케팅 전략을 제안하는 것

2. 데이터 개요

출처: Kaggle "Credit Card Dataset for Clustering"
데이터 크기: 8,950명 고객 × 18개 변수

주요 변수 설명:
BALANCE: 계좌 잔액
PURCHASES: 총 구매 금액
ONEOFF_PURCHASES: 일시불 최대 구매 금액
INSTALLMENTS_PURCHASES: 할부 구매 금액
CASH_ADVANCE: 현금 서비스 금액
CREDIT_LIMIT: 신용 한도
PAYMENTS: 납부 금액
MINIMUM_PAYMENTS: 최소 납부 금액
PURCHASES_FREQUENCY: 구매 빈도
TENURE: 카드 사용 기간

3. 분석 과정

3-1. 데이터 전처리
결측치 처리: MINIMUM_PAYMENTS → 중앙값 대체, CREDIT_LIMIT → 결측 제거
이상치 탐지 (IQR 방식) 및 분포 확인
변수 단위 불균형 확인 후 표준화(StandardScaler) 적용

3-2. 군집화 모델링
Elbow Method를 사용하여 적정 군집 수 탐색
k=5로 설정 (VIP 고객층을 분리하기 위함)
K-Means 알고리즘 적용

3-3. 시각화 및 검증
PCA(주성분 분석)로 차원 축소 후 2D 군집 시각화
군집별 인원 비중, 소비 성향, 결제 방식 분포도 확인

4.결과 요약

Cluster 0 – 현금서비스 의존형 (12%)
Balance·Credit Limit·Cash Advance 모두 높음
소비보다는 단기 자금 조달 목적
👉 리스크 관리 + 카드 사용 전환 유도

Cluster 1 – 저활동 대중층 (35%)
대부분 지표가 평균 이하, 고객 규모 가장 큼
👉 생활밀착형 혜택 제공 (교통, 편의점, 카페)

Cluster 2 – VIP 고소비층 (4%)
Purchases·Payments 압도적, 현금서비스 거의 없음
👉 프리미엄 카드, 마일리지·여행·라운지 혜택

Cluster 3 – 저소비·저한도층 (8%)
낮은 소비, 소극적 사용, Cash Advance 거의 없음
👉 소액 결제 촉진, 연회비 면제, 기본 혜택 유지

Cluster 4 – 저소득·저활동층 (41%)
모든 지표 낮음, 비활성 그룹
👉 첫 사용 포인트 지급, 생활 필수 쿠폰 제공


5. 사용 기술
언어/라이브러리: Python (Pandas, Numpy, Matplotlib, Seaborn, Scikit-learn)

분석 기법:
데이터 전처리 (결측치/이상치 처리, 표준화)
K-Means 클러스터링
PCA 차원 축소 시각화


6. 인사이트

VIP 그룹(Cluster 2)은 고객 수는 적으나, 카드사의 핵심 수익원임을 확인
대규모의 저활동 고객(Cluster 1, 4)은 활성화 전략이 필요
현금서비스 의존형 고객(Cluster 0)은 리스크 관리와 소비 전환 유도가 핵심
