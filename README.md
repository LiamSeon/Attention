# Attention Mechanisms
Practices for attention mechanisms

## 1.Attention Transfer
기존의 Knowledge Distillation의 경우 Soft-max Output을 이용해 Student Model의 퍼포먼스를 Teacher와 비슷한 수준으로 맞추는 모델이었다.

만약 각 Activation Layer의 Activation Tensor 값들이 모델에 영향을 준다면 Attention Map이 Soft-max output보다 더 많은 정보로 Student Model을 학습시킬 수 있을 것이다.

<img width="692" alt="스크린샷 2021-02-14 오후 3 39 02" src="https://user-images.githubusercontent.com/68293683/107870343-c6131f80-6eda-11eb-923a-9a62bf519774.png">

위의 실험을 통해 Attention Map이 모델의 성능에 영향을 준다는 것을 알 수 있다.

그렇다면 이제 Teacher의 Attention Map을 이용해 Student를 학습시키면 된다.

Loss function은 다음과 같다.

<img width="511" alt="스크린샷 2021-02-14 오후 3 39 26" src="https://user-images.githubusercontent.com/68293683/107870350-d4613b80-6eda-11eb-97dc-84747864761a.png">

이 때, 깊이가 같은 경우 매 Activation Layer마다 학습을 진행하고, 깊이가 다를 경우 Group으로 나누어 학습을 진행한다.

<img width="630" alt="스크린샷 2021-02-14 오후 3 39 44" src="https://user-images.githubusercontent.com/68293683/107870355-de833a00-6eda-11eb-931d-e56db15f7e3f.png">

결과적으로 더 좋은 결과가 나오는 것을 볼 수 있다.

<img width="262" alt="스크린샷 2021-02-14 오후 3 46 32" src="https://user-images.githubusercontent.com/68293683/107870454-d24bac80-6edb-11eb-8f01-0b2526e23619.png">
