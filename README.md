## kcbert를 기반으로 만든 distillation 모델

### 연구의 배경
정확도를 올리기 위해서 단순하게 모델의 사이즈를 키우고 있는 텍스트 분석 모델
이로 인해, 딥러닝 모델이 단순하게 크기를 키우면서 생긴 문제들이 생기기 시작한다.

1. 하드웨어 이슈 (메모리 사이즈의 한계)
모델의 사이즈가 커지면서 하드웨어 증설이 필수적으로 요구되고 있음 

2. 성능 저하
단순하게 사이즈를 크게 키운 모델은 과적합(overfitting) 이슈가 발생할 가능성이 높음 

3. 실용적인 문제
지속적으로 증가하는 모델과 데이터의 사이즈는 회사/연구소/대학원 등에서 유지하는 하드웨어 비용이 부담이 될 수 있음 모바일/자동차 같은 환경에서는 GPU 사용에 제한을 받음


### Distillation은 무엇인가
- Teacher 모델의 가중치 정보를 Student 모델에 효율적으로 전달하는 모델
- 지식 증류 모델 내 Teacher 모델과 Student 모델은 Tradeoff 관계 존재
  1. Teacher Network는 정확도가 높지만 연산 비용이 높음
  2. Student Network는 빠른 추론 속도를 보이지만 정확도가 낮음

### Distillation 테스트 파라미터

LAYER - 1,3,6
DIMENSION - 192, 768, 3072

결과적으로, Layer 3, DIMENSION 768이 가장 높은 정확도를 보였음
자세한 내용은 블로그에 추후 업데이트 예정

### 실험 결과
- Distillation 코드를 적용시켜서 새로운 student 모델을 생성하면, 소폭 정확도가 떨어지지만 성능 측면으로는 크게 향상
- Distillation 코드를 학습시킬 때, 도메인 관련 데이터로 학습을 시킬 시 정확도의 저하를 어느 정도 막을 수 있음
⇒ 결론적으로, 실용적인 효율성이 중요한 기업, 기관, 학교에서는 경량화 모델을 사용하는 것이 효율적

### 향후 과제
- 도메인 데이터 위주로 수집 (뉴스, SNS, 위키 등 다양한 텍스트 데이터 수집)
- Distillation 방법론에 Pruning, Quantization 등 다양한 경량화 방법론과 결과 비교
- 실제 기업에서의 텍스트 분류 분석 모델에 적용하는 프로젝트 제안 예정
