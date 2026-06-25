---
type: literature_note
citekey: liIDHNetCNNTransformerHybrid2026
tags:
  - AMC
  - paper
  - IDHNet
  - HybridArchitecture
---
# IDHNet: A CNN-Transformer Hybrid Network With Feature Interaction for Robust Automatic Modulation Classification

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> Automatic Modulation Classiﬁcation (AMC) is a critical enabling technology in modern wireless communication systems, essential for spectrum resource management, signal detection, and adaptive transmission optimization. Recent eﬀorts have focused on hybrid neural architectures to improve AMC performance. However, existing CNN–Transformer designs still exhibit inherent limitations in feature extraction, which hinder eﬀective representation learning of complex I/Q signals and consequently restrict classiﬁcation accuracy and robustness under challenging wireless environments. To address these issues, this paper proposes a high-performance CNN–Transformer hybrid architecture, termed IDHNet. The network consists of two dedicated modules. First, an Inter-branch Fusion Convolution Module (IFCM) is introduced in the Convolutional Stem to extract multi-scale waveform features, where diﬀerent receptive ﬁelds interact during feature construction to form more expressive local representations. Second, HDSFormer is introduced to model non-restricted temporal–channel signal features. This module combines a lightweight attention mechanism with a convolutional front-end to collaboratively capture global context and ﬁne-grained temporal details. Based on this architecture, IDHNet establishes an integrated local–global representation learning pipeline, enabling complementary collaboration between convolution and attention while preserving detailed I/Q waveform information. The experimental results on the RadioML2016.10a, RadioML2016.10b, and RML22 datasets show that IDHNet achieves classiﬁcation accuracies of 63.81%, 65.43%, and 70.92%, respectively, surpassing the state-of-the-art baselines. Furthermore, the proposed model exhibits strong robustness in low signal-to-noise ratio (SNR) conditions and in scenarios involving highly confusable modulation types.

- **저자:** Wentao Li, Zhuoran Cai, Yi Lou, Yun Lin, Guan Gui
- **발표 연도:** 2026
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/RHLH4YBJ)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트
- Convolution stem: I, Q, IQ융합 3가지 path로 설정
- $Result = (I \times Sigmoid(IQ)) + (Q \times Sigmoid(IQ))$
- Point-wise Product를 통해 차원 유지, I와 Q의 독립적인 정보를 유지하고, 융합 채널(IQ융합)을 곱해준 이후 더함
- 이후, Transformer 삽입(EAA와 같이, 연산 복잡도가 낮은 구조 채택)

---
## 📝 내 요약 노트 (Zotero Notes)

# 용어

- ## Convolution stem:
    
    Front-end에 위치하여, convolution layer로 구성된 초기 구조(Low-level Feature=Local Feature 추출 , 다음 layer에 들어갈 수 있도록 Channel 수 조정, Downsampling을 통해 연산량 통제)
    
- ## FLOPs(부동소수점 연산 횟수):
    
    모델이 1회 추론 시 수행하는 덧셈, 곱셈 등의 부동소수점연산 횟수, 하드웨어 독립적인 이론적 지표, 모델의 수학적/구조적 복잡도를 나타냄
    
- ## Inference Time(Latency):
    
    모델이 1회 추론을 완료하는 데 걸리는 실제 시간, 하드웨어 종속적인 물리적 지표, 하드웨어의 최적화/메모리 속도/병렬 처리 효율성을 보여줌
    

# 통신

- ## 16QAM
    
    하나의 Symbol에 4비트(2^4)의 정보를 담음.
    
    I/Q평면에 16개의 constellation point
    
- ## 64QAM
    
    하나의 Symbol에 6비트(2^6)의 정보를 담음.
    
    I/Q평면에 64개의 constellation point
    
- ## 두 방법을 구분 하기 위하여:
    
    64QAM 방식이 16QAM 방식에 비해 I와 Q의 나타낼 수 있는 level이 더욱 높음(유클리드 거리가 더 작고 퍼져있음).
    
    따라서, 매우 국소적인 특징(micro-local)의 차이가 아니라 이보다 큰 심볼 변화(Meso-local)수준을 파악해야함(다음 심볼로 넘어갈 때, 진폭 변화의 level 수준을 파악해야함).


---
## 🖋️ 조테로 하이라이트 & 캡처
![[AMC_Papers/images/image-5-x98-y533.png]]
![[AMC_Papers/images/image-5-x233-y521.png]]
![[AMC_Papers/images/image-5-x236-y540.png]]
![[AMC_Papers/images/image-5-x394-y541.png]]
![[AMC_Papers/images/image-6-x106-y618.png]]
![[AMC_Papers/images/image-6-x123-y350.png]]
![[AMC_Papers/images/image-7-x308-y526.png]]
![[AMC_Papers/images/image-7-x318-y415.png]]
![[AMC_Papers/images/image-7-x380-y157.png]]
![[AMC_Papers/images/image-8-x45-y324.png]]
![[AMC_Papers/images/image-9-x38-y426.png]]
![[AMC_Papers/images/image-9-x49-y496.png]]
![[AMC_Papers/images/image-12-x65-y443.png]]
![[AMC_Papers/images/image-13-x58-y301.png]]
