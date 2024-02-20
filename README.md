# 🏦 금융 CSS(신용평가모형) 개발

고객 금융 활동을 대출등급 기준으로 분석하고,    
그 결과를 바탕으로 신용점수를 산출한 후 신용등급을 재분류합니다 💸

</br>

## 👩🏻‍💻 팀원

<table>
  <tbody>
    <tr>
      <td align="center"><a href="https://github.com/amadosin"><img src="https://avatars.githubusercontent.com/u/157770169?v=4" width="100px;" alt="고경화"/><br /><sub><b>고경화</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/siennavely"><img src="https://avatars.githubusercontent.com/u/130072475?v=4" width="100px;" alt="권은지"/><br /><sub><b>권은지</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/twoibtone"><img src="https://avatars.githubusercontent.com/u/109264568?v=4" width="100px;" alt="이지은"/><br /><sub><b>이지은</b></sub></a><br /></td>
      <td align="center"><a href="https://github.com/heleownae"><img src="https://avatars.githubusercontent.com/u/152258170?v=4" width="100px;" alt="이해원"/><br /><sub><b>이해원 (팀장)</b></sub></a><br /></td>
    </tr>
  </tbody>
</table>

</br>

## 📊 분석 내용
### 1. EDA 및 이상치 탐지, 전처리
- 결측치는 없었으며, 이상치는 EDA 내역과 기술통계를 바탕으로 제거
- 각 컬럼이 독립변수로서 기능할 수 없다고 판단하여 파생변수 다수 생성
- 로그 정규화

![css_eda](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/9333381b-7257-4256-9ebe-6441d7750ea8)
![logstand](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/25bf1b8d-7627-44a4-9d5d-246004aabc3a)

### 2. feature 정의 및 상관관계 분석
- 대출 대비 총상환금
- ✅ 상환부담률 (대출금 대비 총상환이자)
- ✅ 상환율 (대출금 대비 총상환원금)
- 주택소유 여부
- 잔여상환금 대비 연체금액
- 연체계좌 비율 (총계좌수 대비 연체계좌수)

![image](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/1434390a-9da4-443e-96a9-f577ace7daec)

### 3. 모델링 및 평가
- train / test 데이터 분리
- RF, XGB, LGBM 모델 f1 score 비교
  
| RF | XGB | LGBM |
|:------:|:---:|:---:|
| 0.94 | 0.93 | 0.93 |

</br>

### 4. 신용점수화
- 선형회귀를 이용한 feature 별 가중치 도출
- `신용점수 = 상환부담율 * -2.58 + 상환율 * 1.72 + 4.34`

![image](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/b6d84355-2fa6-4ef2-9bef-150a5c35013b)

### 5. 등급 재분류
- DT 기반 기준점 도출

![image](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/4749bfc7-35e3-4bf4-a8fe-d164ffee5a1e)

![newgrade](https://github.com/heleownae/DA_PJT_CSS/assets/152258170/40c8e8b8-c3e3-476b-8b5b-de641632dfdf)

</br>

## 💡 제언
- 등급 재분류 기준점 보완 작업
- 쇼핑 내역, 통신요금 납부 내역 등 대안 평가 지표 개발
- 여신 대출기관의 매출 증대에 기여할 수 있는 고객 세그먼테이션


