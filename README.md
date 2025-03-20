## 스마트 온실 환경 데이터 인공지능 예측 및 시각화 기술 개발

  스마트 온실 환경 데이터 인공지능 예측 및 시각화 기술 개발을 목표로 하는 프로젝트입니다. 

  토마토 선도 농가 4곳의 각 3, 5개년의 환경 데이터를 인공지능 기술을 활용하여 학습시킵니다.

  작물 성장에 최적의 조건을 유지하는 수치를 찾아 자동화시키고 시각화하는 것을 목표로 합니다.

  전북대학교 산학실전캡스톤 프로젝트로 국립농업과학원의 제안을 통해 진행하였습니다.

### 프로젝트 개요
 - **스마트 온실 확대**: 작물 수확량과 노동력 감소를 위한 스마트 온실 ICT 기술 확대.
 - **어려운 구동기 설정**: 경험이 부족한 귀농인과 청년 창업인에게는 어려운 분야.
 - **최적의 생육 환경**: 적합한 구동기 설정값과 내부온도 유지를 위한 수치값 필요.
 - **인공지능 기술**: 선도 농가의 데이터를 분석, 학습하여 최적의 설정값 탐색.

### 개발 과정
 ![Image](https://github.com/user-attachments/assets/e1921fc6-9524-4b79-8542-ddb0e90b5842)
 - **데이터 분석**: 데이터 특성 분석과 상관관계 분석을 통해 모델 학습에 중요한 변수를 선정.
 - **데이터 전처리**: 이상치 제거, 결측치 보간, 스케일링 및 정규화를 이용하여 전처리.
 - **모델 선정**: 시계열 데이터 처리를 위한 모델(RNN,GRU,LSTM)을 비교 후 사용.
 - **학습 및 검증**: 성능이 가장 좋은 LSTM을 사용하여 내부 온도와 구동기 제어값을 예측.
 - **일반화**: 학습 데이터가 없는 농가 환경에서도 모델 성능을 테스트하여 적용 가능성을 검증.
   
### 주요 기능
 ![Image](https://github.com/user-attachments/assets/4b57102f-0675-4000-bf29-78629e62dc1e)
 - **내부 온도 예측**: 농장주가 실시간으로 온실환경을 최적화 할 수 있도록 예측값 제공.
 - **구동기 제어값 예측**: 내부 온도를 유지하기 위한 구동기 제어값 예측.

### 데이터 설명
 시계열 데이터로 이루어진 토마토 농가의 온실 데이터를 활용
 - **외부 데이터**: 외부온도, 풍향, 풍속, 일사량, 누적 일사량, 감우
 - **내부 데이터**: 내부온도, 내부습도
 - **제어 데이터**: 난방온도, 환기온도
 - **구동기 데이터**: 공급온도1, 천창좌개도, 천창우개도, 커튼상개도, 커튼하개도, 측커튼개도, 외부커튼개도 등

### 결과 및 성능 평가
 평가 지표는 Rmse와 R^2를 사용, 평가 기준은 내부온도 예측 오차 0.2이하, 구동기 개도율 오차 5이하
 - **하이퍼 파라미터**: LSTM 학습에 사용되는 파라미터 중 layer가 1 이고 hidden_size가 1024일 경우 우수한 성능
 - **모델 성능**: 내부온도 모델 예측 오차 0.1, 구동기 개도율 오차 4이하로 우수한 성능을 보임
 - **일반화 모델 성능**: 학습 데이터에 포함되지 않은 온실 환경에서도 기존 학습 모델과 비슷한 수준으로 유지

### 모델 학습 코드
  A농가에 대해 내부온도 예측:
  ```bash
  jupyter notebook tomato_train_inner.ipynb
  ```

  전체 농가에 대해 내부온도 예측:
  ```bash
  jupyter notebook tomato_train_all.ipynb
  ```

  전체 농가에 대해 구동기 제어값 예측:
  ```bash
  jupyter notebook tomato_train_double.ipynb
  ```

  D농가에 대해 일반화하여 예측:
  ```bash
  jupyter notebook tomato_normalization.ipynb
  ```

### 학습 환경
 - Colab (A100, L4, T4 GPU)

### 필요 라이브러리
 - Python 3.8+
 - PyTorch
 - Matplotlib
 - Pandas
 - NumPy
