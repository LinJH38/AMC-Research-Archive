---
type: literature_note
citekey: tangReparameterizationCausalConvolutional2024
tags:
  - AMC
  - paper
  - Causal
  - CNN
  - Attention
  - RepCCNet
---
# Reparameterization Causal Convolutional Network for Automatic Modulation Classification

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> With the proliferation of wireless technologies in vehicular networks, robust automatic modulation classiﬁcation (AMC) has become crucial for optimizing spectrum utilization and maintaining reliability. However, AMC in dynamic vehicular channels poses signiﬁcant challenges for traditional machine learning techniques. This paper proposes a novel CNN-based approach named Reparameterization Causal Convolutional Network (RepCCNet) to achieve highly accurate and noise-robust AMC performance. RepCCNet incorporates causal convolutions and structural reparameterization techniques to extract long-term time-domain features. A bottleneck structure with channel attention dynamically calibrates feature channels, retaining only helpful information. Multi-sample dropout is integrated during training to improve generalization capability. We demonstrate RepCCNet’s state-ofthe-art classiﬁcation accuracy on the two widely used datasets, RadioML 2016.10a and RadioML 2018.01a, across varying signalto-noise ratios. Compared to existing methods, RepCCNet achieves highly competitive results compared to state-of-the-art approaches, utilizing fewer than 40 k parameters. Ablation studies validate the contributions of the proposed architectural innovations. This work represents a signiﬁcant advancement toward developing deep learning solutions for robust wireless signal classiﬁcation tasks.

- **저자:** Ning Tang, Xiaoyu Wang, Fei Zhou, Shengyu Tang, Yaohui Lyu
- **발표 연도:** 2024
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/Y6XMDE7Y)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트

- RNN은 병렬 연산 처리가 불가능하므로, CNN을 통해 Inference Time을 낮추는 것은 합리적.
- 저SNR에서 좋은 Classification 능력을 위해, Inductive Bias가 필수.
- Training(ensemble)에서 무겁고 복잡하게 학습하고, Test에서 단일 모델을 채택함으로써 파라미터를 감량시킴.
- Training: Causal 기법, Masking 기법, Ensemble 기법 활용.
- Test: 부차적인 기법들 제거하고, 기존 CNN처럼 연산.
---
## 📝 내 요약 노트 (Zotero Notes)
작성된 요약 노트가 없습니다.

---
## 🖋️ 조테로 하이라이트 & 캡처
![[AMC_Papers/images/image-2-x87-y634.png]]
![[AMC_Papers/images/image-2-x86-y515.png]]
