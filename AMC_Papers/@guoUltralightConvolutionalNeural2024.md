---
type: literature_note
citekey: guoUltralightConvolutionalNeural2024
tags:
  - AMC
  - paper
  - CNN
---
# Ultralight Convolutional Neural Network for Automatic Modulation Classification in Internet of Unmanned Aerial Vehicles

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> Deep learning (DL)-based automatic modulation classiﬁcation (AMC) has made breakthroughs and is generally used for signal detection and recognition in wireless communication systems, unmanned aircraft vehicle (UAV) systems, and other ﬁelds. However, high storage and computational demands limit its use in resource-constrained UAV systems. This article presents an AMC method featuring a streamlined design with lower computational needs, using the ultralight convolutional neural network (ULCNN). This innovative model combines data augmentation, complex-valued convolution, separable convolution, channel attention, and shufﬂing techniques for enhanced performance. The proposed ULCNN model balances efﬁciency and accuracy, with simulations showing it achieves 62.47% accuracy on the RML2016.10a data set using only 9751 parameters. Furthermore, we evaluated the actual speed of ULCNN on a Raspberry Pi, an edge platform with roughly equivalent computing power to a conventional UAV, achieving an inference speed of only 0.775 ms per sample. This high performance, coupled with a signiﬁcantly smaller model size, underscores the potential of ULCNN for integration into resource-constrained UAV systems, thereby enabling rapid and efﬁcient data processing.

- **저자:** Lantu Guo, Yu Wang, Yuchao Liu, Yun Lin, Haitao Zhao, Guan Gui
- **발표 연도:** 2024
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/4DJBZTYN)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트
- Data Augmentation 기법으로, 해당 방식 대신 [[@zhangAutomaticModulationClassification2023]]에서 활용된 RPO 기법 활용.
- 우수한 경량화 기법보다 중요한 것이 효율적인 Structure
- CNN에서 연산 복잡도를 감소시키기 위해, Separable Convolution(PW+DW)기법 활용
- 해당 연구에서도 O(N)에 해당하는 Attention기법(Channel Attention)을 사용하였음. 결국 경량화를 시키더라도, CNN만 활용한 구조보다 CNN+Transformer(Attention)의 Hybrid Architecture가 좋음.

---
## 📝 내 요약 노트 (Zotero Notes)
작성된 요약 노트가 없습니다.

---
## 🖋️ 조테로 하이라이트 & 캡처
![[AMC_Papers/images/image-3-x317-y627.png]]
> [!quote]|#ffd400
> compact structural design as a fundamental aspect of lightweight model optimization techniques ([p.3](zotero://open-pdf/library/items/K73ED95L?page=3))
> **메모:** 1. 우수한 경량화 기법을 동원하더라도, 근본적인 Structure가 비효율적이라면 비효율적임. 따라서 compact structure 설계에 관심 가져야함.
![[AMC_Papers/images/image-3-x316-y567.png]]
![[AMC_Papers/images/image-3-x317-y455.png]]
![[AMC_Papers/images/image-3-x316-y352.png]]
![[AMC_Papers/images/image-3-x352-y36.png]]
![[AMC_Papers/images/image-4-x60-y539.png]]
![[AMC_Papers/images/image-5-x89-y519.png]]
