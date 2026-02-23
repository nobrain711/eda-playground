# 전세계 행복 지수 (2015 ~ 2024) EDA

World Happiness Report (2015–2024) 데이터를 기반으로 팀원들이 수행한 EDA 결과를 모아
통합 리포트(EDA Report)를 완성하는 프로젝트입니다.

- 데이터: World Happiness Report (2015–2024)
- 목표: 행복 점수/순위 변화 패턴, 주요 지표 관계, 변동성, 코로나 전후 비교를 종합적으로 정리
- 산출물: 개인별 분석 노트북 + 취합 리포트(예정)

---

## Kaggle Dataset
- 2015 ~ 2019: https://www.kaggle.com/datasets/unsdsn/world-happiness
- 2020 ~ 2024: https://www.kaggle.com/datasets/samithsachidanandan/world-happiness-report-2020-2024

---

## Data Policy
- Kaggle 원본 데이터는 Git에 커밋하지 않습니다.
- 분석은 통합 데이터셋 `data/happiness_2015_2024.csv` 기준으로 진행합니다.

---

## 팀원

| GitHub | dhksrlghd | rusidian | nobrain711 | imseunghyeon264 | ParkMinSeon22 | ch3477-sudo |
|---|---|---|---|---|---|---|
| Profile | @dhksrlghd | @rusidian | @nobrain711 | @imseunghyeon264 | @ParkMinSeon22 | @ch3477-sudo |
| Name | 홍원기 | 장한재 | 조동휘 | 임승현 | 박민선 | 윤찬호 |

---

## Final Outputs
- 통합 데이터셋: `data/happiness_2015_2024.csv`
- 최종 취합 리포트: `reports/eda_report.md` (업데이트 예정)
- 핵심 인사이트 요약: `reports/key_insights.md` (업데이트 예정)
- 시각화 이미지: `reports/figures/` (업데이트 예정)

---

## Reports / Notebooks

### 1) 데이터 통합/정제
- `HongWanGi/01_World_Happiness.ipynb`
- `YunChanHo/01_merge_standardize.ipynb`

### 2) 전체 EDA 리포트
- `YunChanHo/02_eda_report.ipynb`
- `ParkMinSeon/eda_report.ipynb`

### 3) 변동성 분석 + 코로나 전후 해석
- `JangHanJae/eda_volatility_covid_interpretation.ipynb`
- `JangHanJae/eda_volatility_covid_interpretation.md`

### 4) 추가 분석/정리
- `LimSeungHyeon/eda_analysis.ipynb`
- `LimSeungHyeon/manual.md`

---

## How to Run (Recommended Order)

- Step 1) 데이터 통합/정제
  - `YunChanHo/01_merge_standardize.ipynb` 또는 `HongWanGi/01_World_Happiness.ipynb`
  - 결과물: `data/happiness_2015_2024.csv`

- Step 2) 전체 EDA 리포트
  - `YunChanHo/02_eda_report.ipynb`
  - `ParkMinSeon/eda_report.ipynb`

- Step 3) 변동성 + 코로나 전후 비교 (선택)
  - `JangHanJae/eda_volatility_covid_interpretation.ipynb`

- Step 4) 추가 분석/정리 (선택)
  - `LimSeungHyeon/eda_analysis.ipynb`
  - `LimSeungHyeon/manual.md`

---

## Notebook → Report Mapping (Draft)
- Data Overview / Data Quality: `01_merge_standardize.ipynb`, `01_World_Happiness.ipynb`
- Descriptive Statistics / Univariate / Bivariate / Correlation: `02_eda_report.ipynb`, `eda_report.ipynb`
- Volatility Analysis / COVID Before-After: `eda_volatility_covid_interpretation.ipynb`, `eda_volatility_covid_interpretation.md`
- Appendix (추가 분석/참고): `eda_analysis.ipynb`, `manual.md`

---

## EDA Report Structure
최종 취합 리포트는 아래 구조를 기준으로 정리합니다.

- Executive Summary (핵심 결론)
- Introduction (분석 목적/질문)
- Data Overview (스키마 통일, 컬럼 정의)
- Data Quality (결측/중복/타입/이상치)
- Descriptive Statistics (기술통계/분포)
- Univariate Analysis (수치/범주)
- Bivariate Analysis (관계/비교)
- Correlation Analysis (상관/해석)
- Volatility Analysis (rank/score 변동성 Top 국가)
- COVID Before/After (2015–2019 vs 2020–2024)
- Conclusions & Recommendations
- Appendix (추가 분석/참고)

---

## Used Tech
- Language: Python
- Notebook: Jupyter Notebook
- Data Handling: pandas, numpy
- Visualization: matplotlib, seaborn
- Machine Learning (optional): scikit-learn

---

## Key Insights

- 행복지수(Happiness Score)는 `GDP`, `Life_Expectancy`, `Social_Support`와 강한 양의 상관관계를 보였습니다.
  - 결과: `GDP`(≈ 0.79), `Life_Expectancy`(≈ 0.68), `Social_Support`(≈ 0.66)가 상대적으로 높은 상관을 보였습니다.
  - 권장: 향후 분석/모델링에서는 위 3개 지표를 핵심 설명변수 후보로 우선 고려합니다.

- `GDP`와 `Life_Expectancy`는 서로 높은 상관관계를 보여 다중공선성 가능성이 있습니다.
  - 결과: `GDP` ↔ `Life_Expectancy` 상관이 높게 나타났습니다(≈ 0.81).
  - 권장: 선형 회귀 기반 모델을 사용할 경우 Ridge/Lasso 등 규제(regularization)를 적용하거나,
    Tree 기반 모델로 Feature Importance를 함께 확인합니다.

- `Generosity`, `Corruption`(부패 인식) 등 일부 주관적/인식 지표는 핵심 경제·사회 지표 대비 직접 상관이 낮게 나타났습니다.
  - 결과: 경제/건강/사회적 안전망 지표 대비 행복지수와의 직접 연관이 상대적으로 약했습니다.
  - 권장: “단독 지표”로 해석하기보다, 지역/대륙/소득수준 등으로 층화(stratification)하여 조건부로 해석합니다.

- 변동성(Volatility) 분석을 통해 연도별 순위/점수 변화가 큰 국가를 식별하고, 시간 흐름을 라인 차트로 확인했습니다.
  - 결과: rank/score 변화량(평균 |Δrank|, 최대 |Δrank|, 표준편차 등) 기반으로 변동성 Top N 국가를 비교했습니다.
  - 권장: 변동성이 큰 국가들은 외부 이벤트(정치/경제/보건 등)와 함께 해석할 수 있도록 보조 지표(거시경제/분쟁/팬데믹)를 추가합니다.

- 코로나 전/후(2015–2019 vs 2020–2024) 비교를 통해 분포 변화와 변동성 변화 여부를 점검했습니다.
  - 결과: KDE/Boxplot 및 분산/꼬리 지표로 분포 차이를 비교하고, “순위 변동성 자체” 변화도 확인했습니다.
  - 권장: 전/후 비교 시 표본 국가 수 변화, 결측/스키마 차이를 함께 통제하고 동일 기준으로 재현합니다.

---

###  폴더 구조
```
project/
|
├─── data/              
├─── HongWanGi          
├─── JangHanJae         
├─── JoDongHwi          
├─── LimSeungHyeon      
├─── ParkMinSeon        
├─── YunChanHo          
├─── requirements.txt   
├─── LICENSE            
├─── .gitignore
└─── README.md
```

---

## Getting Started (FAQ)

- Q. `data/happiness_2015_2024.csv`가 없어요.  
  - A. `How to Run`의 Step 1(통합/정제) 노트북을 먼저 실행해 통합 CSV를 생성하세요.

- Q. geopandas 설치 중 에러가 나요.  
  - A. conda 환경에서 `conda install geopandas` 후 `pip install -r requirements.txt` 순서로 설치를 권장합니다.

- Q. 어떤 노트북부터 실행해야 하나요?  
  - A. README의 `How to Run (Recommended Order)` 순서를 따르세요.