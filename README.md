# Attention
Practices for attention mechanisms

## PAYING MORE ATTENTION TO ATTENTION : IMPROVING THE PERFORMANCE OF CONVOLUTIONAL NEURAL NETWORKS VIA ATTENTION TRANSFER.
기존의 Knowledge Distillation의 경우 Soft-max Output을 이용해 Student Model의 퍼포먼스를 Teacher와 비슷한 수준으로 맞추는 모델이었다.

만약 각 Activation Layer의 Activation Tensor 값들이 정확도에 영향을 준다면 Soft-max output보다 더 많은 정보로 Student Model을 학습시킬 수 있을 것이다.
