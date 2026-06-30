---
type: literature_note
citekey: xinCPPCNetHighPerformanceLowComplexity2025
tags: [AMC, paper]
---
# CPPCNet: High-Performance and Low-Complexity Automatic Modulation Classification for Resource-Limited IoT Communication

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> Automatic modulation classiﬁcation (AMC) enables the identiﬁcation of modulation schemes without prior information, facilitating efﬁcient signal processing. Recently, deep-learning (DL)-based AMC has signiﬁcantly advanced signal detection and recognition across various domains, including Internet of Things (IoT) systems and industrial cognitive communication systems. While high-performing AMC models achieve remarkable accuracy, their substantial storage and computational demands hinder deployment in resource-limited IoT communication systems. To address this challenge, we propose CPPCNet, a high-performance, lightweight complex-valued partial pointwise convolutional neural network. By leveraging complex-valued operations for automatic feature extraction, CPPCNet preserves phase information, enhancing classiﬁcation performance. To alleviate the computational burden of complex-valued operations in resource-limited IoTs, we introduce complex-valued partial pointwise convolution (CPPC), which optimally balances accuracy and model complexity. Experimental results show that CPPCNet, with only 65 302 parameters, achieves a state-of-the-art (SOTA) accuracy of 66.38% on RML2016.10b among all existing AMC models. On RML2016.10a, it also achieves a strong performance with an accuracy of 62.25%. Furthermore, it achieves 83.5% accuracy on the HisarMod2019.1 dataset, which includes more realistic channel impairments, outperforming existing lightweight AMC models in both accuracy and inference speed. These results highlight CPPCNet’s strong generalization ability and its ability to balance performance and efﬁciency, making it a promising solution for AMC applications in resource-constrained and dynamically changing environments.

- **저자:** Guangda Xin, Zhuoran Cai, Yi Lou, Chuan Wang
- **발표 연도:** 2025
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/MWDJAFGR)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트

- 해당논문은 I/Q 신호의 위상과 진폭이 분류 정확도를 높일 수 있다는 믿음하에, complex-valued로 모델을 처음부터 끝까지 구성하였다. 다만, 연산량을 최소화 하기 위해, DSC(Depthwise Separable Convolution)의 설계철학을 complex-valued로 끌고 왔다. 뿐만 아니라, Depth-wise Convolution 방식으로 PC(real-valued Partial Convolution)방식을 채택하여 연산량을 극소화 했고, Point-wise Convolution 방식으로 CPWC(Complex-valued Point-wise Convolution)의 kernel size를 1로 설정하여, 연산량을 극소화 했다.
- 기존 모델들이 real-valued만 사용했다는 점을 지적하고(Novelty), 연산량을 극소화하고 정확도를 높혀 실효성을 더했다(Contribution).
- CNN(Front-End)를 Complex-valued로 구성(Complex Embedding -> CPPC Block)이후, Transformr(Back-End)를 통해 기존 모델이 지닌 global-information의 부재를 해결. 해당 기법을 통해 아날로그 신호의 분류 정확도를 높일 수 있고, CBN(Complex Batch Normalization)+CReLU(Complex ReLU)를 통해 저SNR에서 강건성 확보 가능.

---
## 📝 내 요약 노트 (Zotero Notes)

## 용어

- ## PC(Partial Convolution)
    
    논문 [Image Inpainting for Irregular Holes Using Partial Convolutions]에서 처음 소개.
    
    기본 Convolution은 모든 채널에 대해 공간적(spatial) 특징을 추출했지만, 신경망이 깊어질수록 채널 간 비슷한 정보를 담는 중복성(Redundancy)문제가 발생함. 이를 해결하기 위해, ‘Masking 부분을 제외하고 유효한 픽셀 범위에만 선택적으로 Convolution 연산 진행’
    
- ## Whitening
    
    데이터 분포를 ‘원점에서’, ‘타원형 -> 원형’으로 만드는 행위.
    
    (1) z-E[Z] 수식을 통해, 데이터를 원점으로 끌고 옴.
    
    (2) (Covarianc Matrix)^(-1/2)를 곱해줌으로써, 차원 간의 상관관계를 없앰(->원형).
    
- ## Pooling:
    
    공간적 또는 시간적 차원을 축소하여, 파라미터를 감소시켜 overfitting을 방지한다(작은 변화에 덜 민감하게 만든다).
    
    ‘어떤 크기의 창(window)으로 얼마나 이동(stride)하며 연산할 것인가’에 따라 출력되는 차원이 달라짐.
    
- ## Adaptive Pooling:
    
    기존 Pooling은 window, stride를 상수로 두고, 출력되는 차원이 변수로 달라짐.
    
    이를 보완하여 ‘출력이 어떤 크기가 되어야 하는가’(출력되는 차원)만 상수로 결정하여, window, stride가 변수로 달라짐.


---
## 🖋️ 조테로 하이라이트 & 캡처
![[AMC_Papers/images/image-4-x381-y274.png]]
![[AMC_Papers/images/image-4-x380-y203.png]]
![[AMC_Papers/images/image-5-x120-y607.png]]
> [!quote]|#ff6666
> This article aims to design a lightweight model that achieves high recognition performance, strong robustness, and low complexity. ([p.5](zotero://open-pdf/library/items/B5ICKK7G?page=5))
> **메모:** [Contribution]
1. 기존의 논문들은 real 기반 I/Q 신호의 특징을 추출했음.

2. 해당 논문에서는 I/Q의 복소수 형태(amplitude, phase)가 중요함을 인지하고, 이를 기반으로 특징 추출

3. 연산량이 높아짐에도 불구하고, 당시 ai 분야에서 혁신적인 경량화 모델인 FasterNet을 Complex valued 버전으로 변형(=Novelty)하여, 연산량을 낮춤.
![[AMC_Papers/images/image-5-x71-y107.png]]
![[AMC_Papers/images/image-5-x342-y375.png]]
![[AMC_Papers/images/image-5-x310-y62.png]]
![[AMC_Papers/images/image-6-x68-y37.png]]
![[AMC_Papers/images/image-6-x387-y722.png]]
![[AMC_Papers/images/image-6-x336-y695.png]]
![[AMC_Papers/images/image-6-x341-y342.png]]
![[AMC_Papers/images/image-6-x306-y129.png]]
![[AMC_Papers/images/image-7-x429-y653.png]]
![[AMC_Papers/images/image-7-x343-y528.png]]
![[AMC_Papers/images/image-7-x438-y534.png]]
> [!quote]|#ffd400
> This suggests that excessive channel expansion may lead to overparameterization and redundant representations, which do not benefit classification performance under the given training setup. On the other hand, reducing r to 0.125 degrades performance slightly, indicating an under-representation of critical features. ([p.10](zotero://open-pdf/library/items/B5ICKK7G?page=10))
> **메모:** 1. PC가 부차적인 효과로 Pooling같은 기능을 수행함: param 감소 -> overfitting 피함.
