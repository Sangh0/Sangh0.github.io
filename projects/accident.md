---
layout: project
type: project
image: img/accident/accident.png
title: "Object Detection for Understanding Scene on Road"
date: 2023.01
published: true
labels:
  - Real-time Object Detection
  - Car Addident Detection
summary: "자동차의 안전한 도로 주행을 위해 도로 위 위험 요소를 탐지하는 모델 구축"
---

<img class="img-fluid" src="../img/accident/accident_ex.png">

### 담당 역할  
- 유튜브를 활용해 데이터 수집
- 데이터 전처리 및 Labeling
- YOLOv7 학습을 위한 환경 세팅
- 학습 및 결과 분석, 하이퍼파라미터 튜닝


### 데이터셋 및 성과
- 무단횡단 보행자, 공사 현장, 사고 3개 클래스 탐지
- 무단횡단 보행자, 공사 현장 탐지 결과에서 Accuracy 85%
- 사고 탐지 결과에서 80 mAP, Accuracy 95%


### 회고
- Problem 1. 부족한 데이터셋
  - 사고 이미지를 수집하기 위해 유튜브 영상을 이미지로 변환
  - Sequence 기준으로 사고 장면 데이터 수집
  - 이후 성능 평가할 때 Sequence 중 하나의 이미지라도 탐지하면 Correct라고 판단하는 Metric 정의

- Problem 2. 오래 소요되는 Labeling
  - 약 500장의 이미지를 먼저 수집하고 Labeling 한 후, 학습하면서 하이퍼파라미터 튜닝을 진행
  - 이후 별도로 추가한 이미지는 Inference를 진행해 자동으로 Labeling이 되도록 설계
  - 100%의 이미지를 한 번에 Labeling하는 것보다 50% 또는 일부를 Labeling, 학습하고 그 외의 이미지들에 대해 Inference를 진행해 Labeling하는 것이 훨씬 더 효율적
  
- Problem 3. 낮은 탐지 정확도
  - 무단 횡단 보행자, 공사 현장, 사고 탐지의 경우는 과탐을 할 경우 큰 문제가 없어 과탐을 위해 즉, Recall Score를 올리기 위해 classification, objectness loss function에서 positive weight를 1.0에서 3.0으로 설정
  - 사고에서 전복의 경우에 대한 성능을 살펴보았으나 차량 하부 부분이 대부분 검은색인 탓에 정상적인 검은색 차량을 모델은 전복이라고 탐지를 하는 경우 발생
  - 그래서 사고 클래스를 전복, 전면 파손, 후면 파손, 정상, 버스 및 트럭으로 세분화시켜 정상 차량에 대한 오탐을 줄이도록 유도


### 시기 및 사용 기술
- 진행 기간: 2022.09.01 ~ present
- 인원: DL (3)
- 사용 기술: PyTorch
- 모델: YOLOv7
