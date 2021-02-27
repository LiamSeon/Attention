# Attention Mechanisms
Practices for attention mechanisms


## 0. Scaled dot attention

## 1. Multi-head attention

## 2. Why Self Attention?
Attention Mechanism이 자연어 처리에서 주어와 동사의 거리가 긴 문장을 처리하는 능력은 RNN과 동일하지만

중의어의 Disambiguity를 해소한다는 논문이다.

## 3. Pay less attetion with lightweight and dynamic convolutions


## 4. SENet

<img width="856" alt="스크린샷 2021-02-27 오후 10 08 06" src="https://user-images.githubusercontent.com/68293683/109388088-48bec480-7948-11eb-85ae-afb85558e6a8.png">

Attention Mechanism을 사용하지는 않았지만, Residual Net 대신 새로운 Inception Network를 제공함으로써 더 나은 성능을 보이는 모델이다. 뒤에 나오는 Attention Based Model이 이를 개조한 것이니 설명하겠음.

<img width="259" alt="스크린샷 2021-02-27 오후 10 08 28" src="https://user-images.githubusercontent.com/68293683/109388094-5411f000-7948-11eb-9d02-0b31d9f6b637.png">

X는 H'* W' * C' 에 속한다 할 때, V = [ v1, v2, ..., vC ]이고 vk는 각각 커널이라 하자.

한 커널을 각각의 X의 채널에 Convolution한 후 나온 값들을 더하면 하나의 H * W 에 해당하는 Feature Map을 만들 수 있다.

이렇게 나온 C개의 Feature Space를  U = [ u1, u2, ..., uC]라고 하자.

이 때 U의 각각의 feature map은 커널 연산만을 수행했으므로 Local 하다.

이러한 점을 Mitigate하기 위해 Global Average Pooling을 수행한다.

이렇게 나온 C차원의 벡터를 Z라 하자. 그러면 이제 각 채널의 Dependent한 정도를 표현해야하는데, 이 때에 서로 Non-linear한 관계도 잡아야 하기 때문에

LSTM에서 사용되는 Gate Mechanism이 사용되었다.

![image](https://user-images.githubusercontent.com/68293683/109388149-a7843e00-7948-11eb-88bd-3d31846b1f47.png)

그렇게 나온 Gate output을 Feature Map U를 Rescaling 하는 데에 사용한다.

<img width="228" alt="스크린샷 2021-02-27 오후 10 13 33" src="https://user-images.githubusercontent.com/68293683/109388199-0a75d500-7949-11eb-82a6-4094383a79db.png">

즉 Inception Block대신 SE block을 사용한다고 보면 된다.



## 4. CBAM


## 5. GSoP

## 6. GE

## 8. ECA-net
1D convolution of K사이즈 필터를 이용한다. 여기서 K는 얼마나 많은 neighbor가 참여하는지를 보는 것

## 9. Attention Transfer
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
