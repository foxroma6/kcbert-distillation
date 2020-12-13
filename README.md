# distillation-project

Distillation은 딥러닝 모델의 경량화 기법

설명 링크: https://medium.com/huggingface/distilbert-8cf3380435b5
논문 링크: https://arxiv.org/abs/1910.01108

대표적인 경량화 기법으로는,
1. Pruning - 불필요한 노드를 제거
2. Quantization - 데이터의 차원을 낮추는 방법 (24 bits 사진 -> 8 bits 사진으로 낮춤)
3. Knowledge Distillation - 가벼운 Student 모델을 생성, Teacher 모델의 가중치를 전달해주는 방법

Distillation 코드
1. 텍스트 데이터 전처리 후, Sentence 데이터로 구성
2. Sentence 데이터를 Teacher 모델 내에 있는 단어로 변형시킨 후, binarized_text 파일로 저장
3. 각 토큰의 빈도 수를 token_counts 파일로 저장
4. Teacher 모델의 training configuration과 비슷한 Student 모델의 Training configuration 구성

distillation parameter 조정
layer - 1,3,6
dim- 3072, 768, 192

변경하면서 테스트 

성능 비교 시, 단순하게 파라미터의 숫자가 많은 layer 6, dim 3072 보다
layer 3, dim 768이 검증 정확도도 가장 높으며 동시에 속도도 상당히 빠른 것으로 나타났다.

