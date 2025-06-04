# 🏢 기업 성공 확률 예측 해커톤: 미래의 성공기업을 발굴하라!

![image](https://github.com/user-attachments/assets/ac5ed769-105d-4454-8276-9cf913c20a14)

`pullic : 20위`

![image](https://github.com/user-attachments/assets/e7fb12ba-c57d-49d2-aa78-b21397cdbec5)

`private : 49위`

## 📝 대회 개요
- 공식 사이트 : [링크](https://dacon.io/competitions/official/236475/overview/description) <- `클릭`
- 주최 : 데이콘
- 목적 : 기업의 다양한 데이터를 기반으로 기업의 성공 여부를 분류하는 AI 알고리즘을 개발
- 대회 기간 : 2025.04.01 ~ 2025.05.30
- 참여 기간 : 2025.04.14 ~ 2025.05.16

## 🧾 데이터(train.csv)
| #   | Column                   | Non-Null Count   | Dtype    |
|-----|--------------------------|------------------|----------|
| 0   | ID                      | 4376 non-null   | object   |
| 1   | 설립연도                 | 4376 non-null   | int64   |
| 2   | 국가                     | 4376 non-null   | object  |
| 3   | 분야                     |3519 non-null   | object   |
| 4   | 투자 단계                | 4376 non-null   | object  |
| 5   | 직원 수                  | 4202 non-null   | float64    |
| 6   | 인수여부                 | 4376 non-null   | object  |
| 7   | 상장여부                 | 4376 non-null   | object  |
| 8   | 고객수(백만명)            | 3056 non-null   | float64    |
| 9   | 총 투자금(억원)           | 4376 non-null   | float64    |
| 10  | SNS 팔로워 수(백만명)     | 4376 non-null   | float64    |
| 11  | 기업가치(백억원)          | 3156 non-null   | object   |
| 12  | 성공확률                  | 4376 non-null   | float64   |


## 👓 EDA
| ![image](https://github.com/user-attachments/assets/ef7f14d4-640e-4627-ae5e-6b4a40c3a5d5) | ![image](https://github.com/user-attachments/assets/7aad4d8d-f869-41ec-90aa-c134325cce61) |
|--------------------------------------------------------|--------------------------------------------------------|



## 📦 전처리
- 결측값 처리(성능 테스트를 통해 직원수, 기업가치 결측값 유지)
- 파생변수 생성
  - 기업_연령
  - 투자금_대비_연매출
  - 연매출_대비_기업가치
  - 고객수_대비_연매출
- 원저라이징
- 로그 변환
- 범주형 변수 처리
- 정규화(Robust Scaler)


## 🤖 모델링
```python
model = RandomForestRegressor(n_estimators=75,
                              max_depth=25,
                               random_state=42)
```

## 🔬 드랍 테스트 (제거 칼럼)
- 투자단계
- 분야
- SNS 팔로워 수(백만명)
- 고객수(백만명)
- 설립연도


## 🎯 결과
### ⚖️ 평가 지표 (Weighted MAE)
- Public Score: **0.20917** (20위)
- Private Score: **0.21433** (49위)

## 🤯 후기
- Weighted MAE가 평가 산정이다보니 정답값을 모르는 입장에서 평가지표를 정하기 어려움
- 그래서 하나씩 실험해보며 제출하다보니 243번 제출하게 됨
- 이러한 방식으로 Public Score를 올리는 것을 목적으로함
- 하지만, 과적합 발생으로 Private Score에서 점수가 많이 떨어짐
- 단순히 Public Score를 올리는 것이 성능 향상을 의미하지 않음을 느낌
