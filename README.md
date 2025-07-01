# Sentence-Ordering-Ensemble-Model
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)

![Image](https://github.com/user-attachments/assets/79d3943d-654e-4f58-b843-cd93bdf630ed)

## 대회 정보

[문맥 기반 문장 순서 예측 AI 경진대회](https://dacon.io/competitions/official/236489/overview/description)

[주제] <br>
뒤섞인 한국어 문장의 올바른 순서를 예측하는 AI 알고리즘 개발

[설명] <br>
논리적 순서 없이 제시된 4개의 한국어 문장을 입력으로 받아 가장 자연스러운 문장 순서를 정답 인덱스 배열로 예측하는 AI 알고리즘을 개발

[대회 기간] <br>
2025년 05월 07일 ~ 2025년 06월 30일

## 대회 전략

1. 모델 선정 및 성능 평가 <br>
   -한국어 처리에 특화된 8개의 사전 훈련된 인코더 모델을 대상으로 베이스라인 성능을 평가하여, 가장 우수한 성능을 보인 상위 3개 모델 선정 <br><br>
2. Pairwise Learning 기반 파인튜닝 <br>
   -문장 순서 예측 문제를 "두 문장 중 어느 것이 먼저 와야 하는가?"라는 이진 분류 문제로 변환하여 접근 <br>
   -다양한 거리(연속, 비연속, 최대 거리)의 문장 쌍과 hard negative 샘플을 포함한 훈련 데이터셋을 생성하고, 선정된 3개 모델 각각을 개별 파인튜닝 <br><br>
3. 순열 기반 앙상블 예측 <br>
   -추론 단계에서는 모든 가능한 문장 순열(24가지)을 평가 <br>
   -각 순열에 대해 연속된 문장 쌍들의 확률을 파인튜닝된 3개 모델로 계산하고, 이를 곱하여 해당 순열의 점수를 산출한 후 가중 평균 기반 소프트 보팅으로 최종 예측 <br><br>
4. 저신뢰도 샘플 재처리 <br>
   -앙상블 모델의 예측 신뢰도가 50% 미만인 경우, QWEN2.5 14B를 활용한 재예측 수행 <br><br>

## 대회 결과 

[Private 34th] Score 0.80561

## 기타

개발 환경: Colab(A100)

선정 모델:
- https://huggingface.co/klue/roberta-large
- https://huggingface.co/kykim/bert-kor-base
- https://huggingface.co/kykim/electra-kor-base

파인튜닝 모델:
- https://huggingface.co/sebalnakji/roberta-large-pt
- https://huggingface.co/sebalnakji/bert-kor-base-pt
- https://huggingface.co/sebalnakji/electra-kor-base-pt

재예측용 모델:
- https://huggingface.co/Qwen/Qwen3-14B
  
  
  
  
