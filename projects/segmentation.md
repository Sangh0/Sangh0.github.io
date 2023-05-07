---
layout: project
type: project
image: img/segmentation/segmentation.png
title: "Semantic Segmentation for Autonomous Driving"
date: 2022.03
published: true
labels:
  - Real-time Semantic Segmentation
  - Cityscapes
summary: "자율 주행을 위한 실시간 Semantic Segmentation 모델 연구"
---

<img class="img-fluid" src="../img/segmentation/seg_ex.png">

### 담당 역할  
- Real-time Semantic Segmentation 논문 리뷰 및 구현
- 성능 향상을 위한 Method 연구
- 모델 학습 및 결과 분석, 하이퍼파라미터 튜닝


### 회고
- Real-time Semantic Segmentation의 Architecture는 일반적인 모델에 비해 Attention module, Feature Refinement module 등 효율적인 구조로 이루어짐
- OHEM CE loss와 Data Augmentation이 성능 개선에 효과적
- 비슷한 특성을 가지는 클래스는 합치거나 Ignore index 지정을 통해 학습을 시키는 것이 더 효과적


### 시기 및 사용 기술
- 진행 기간: 2022.03.01 ~ 2022.06.20
- 인원: DL (1)
- 사용 기술: PyTorch
- 모델: SegNet, BiSeNet, BiSeNetV2, PP-LiteSeg
