## HOLC Redlining → Vegetation Deficit → Urban Heat → Health&Life Disparity
A spatial causal analysis examining how historical HOLC redlining grades propagate through vegetation deficit and urban heat exposure to produce present-day health&life inequities across 108 U.S. cities. (13,000+ census tracts)
## Research Overview - Serial Mediation Framework
HOLC Grade → NDVI Deficit (M1) → LST Deviation (M2) → Health&Life Outcomes


## Holc Readling → 식생 지수 → 지표면 온도 → 보건 및 생활 취약성
HOLC 레드라이닝 등급으로 인한 약 100년간의 지역별 식생 편차를 매개로 야기된 지표면 온도 불평등과 이를 매개로 다시한번 보건 및 생활 취약성이 받는 영향을 분석한 공간 인과 분석 연구입니다. 미국 108개도시, 13518개의 센서스 트랙을 대상으로 분석하였습니다.

## 연구 개요 - 직렬 매개 모형 (serial mediation)
HOLC 등급 → NDVI 편차 (M1) → LST 편차 (M2) → 건강 및 생활 결과
- 등급 간 비교: Kruskal-Wallis + Mann-Whitney U (Bonferroni 보정)
- 파생변수: PCA 기반 사회취약성 지수, 환경적 레드라이닝 지수 (ndvi_holc)
- 회귀분석: Forward Stepwise OLS → 이차다중회귀모형 (R²=0.426)
- 비선형 임계점: LST 반응 변곡점 ndvi_diff = −0.416
- 매개분석: 4단계 Baron-Kenny 직렬 매개 + Sobel Test + Bootstrap CI
- 머신러닝: GridSearch 기반 (RF, ExtraTrees, GBM, XGBoost, LightGBM) + 도시 단위 Group K-Fold CV + 하드/소프트 보팅 (Test R²=0.485)
- PSM 검토: A <-> D 등급 성향점수 추정 (AUC=0.903, 극단적 분리 확인)

## 사용 기술
Python: OLS, Machine Learing, Matplotlib

## 주요 결과
- HOLC D등급 트랙은 A등급 대비 유의하게 낮은 NDVI, 높은 LST 확인 (p<0.001)
- ndvi_diff가 −0.416에 가까워질수록 LST 편차 급등
- 변곡점 이후 LST 감소 (고층 건물 그늘 효과) -> 열취약한 지역은 최고 밀집 지역이 아닌 변곡점 주변부
- 지역별 변곡점 상이: 서부(건조기후)는 소량 녹지 손실에도 민감, 북동부(수목 밀도 높음)는 상대적 회복력 높음
- HOLC → NDVI → LST 매개비율 104% (억압 효과): 녹지 통제 시 HOLC 직접 경로 부호 역전 & Bootstrap 95% CI [0.436, 0.496], 0 미포함
- NDVI → LST → Health&life 매개 분석에서 수면 부족, 식량 불안정, 주거 불안정 등 주요 보건 및 생활 취약성 변수에서 완전 매개 확인
- 최종 4단계 직접 매개 분석 (HOLC 등급 → NDVI 편차 (M1) → LST 편차 (M2) → 건강 및 생활) 결과: 총 15개 변수 중 14개 변수에서 부분 매개 작용 확인
    - 환경 경로 외 경제적 고립, 의료 인프라 격차 등 독립적 사회경제 경로 병존

## 결론
- 과거 holc 등급은 100년동안 지역간 식생 지수의 편차를 야기하여 이를 완전 매개로 현재의 LST에 영향을 주고 있음.
- 식생 지수는 지표면온도를 완전 매개로 하여 수면부족, 식량불안정 경험률, 주거불안정 경험률 등을 야기하고 있음.
- holc 등급이 현재의 보건&생활 취약성으로 연결되는 매개에는 '식생 편차 및 지표면 온도' 외에 기타 매개 요인이 있는것으로 보임.
- 폭염 피해 정책의 경우 선형적 지원이 아닌 변곡점을 기준으로 한 취약 지역을 타겟화하여 진행될 필요가 있음.
- 현재 실행되는 정책이 시간의 흐름 속에 더 큰 변화를 야기하여 새로운 변수에 영향을 줄 수 있음을 고려해야 함.

## 내 역할 (4인 구성)
- 메인 역할: 팀장, 데이터 전처리, 회귀분석 및 머신러닝, 매개분석(sobel test, bootstrap)
- 보조 역할: EDA, PCA, 지역별 변곡점 도출
