---
type: literature_note
citekey: liComplexValuedTransformerAutomatic2024
tags:
  - AMC
  - paper
  - Transformer
  - ComplexValued
  - CV-TRN
---
# A Complex-Valued Transformer for Automatic Modulation Recognition

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> 

- **저자:** Weihao Li, Wen Deng, Keren Wang, Ling You, Zhitao Huang
- **발표 연도:** 2024
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/KWSNBJQ2)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트

- 해당 Transformer only architecture는 Inference Time이 매우 높아서 활용 못 함. O(n^2)로 naive하게 넣으면 안 됨. EAA를 Complex data에 알맞게 수정하거나, Down-sampling 이후 넣어보는 등 Transformer의 Long-term dependency 기능은 유지한 채로, 연산량을 억제하는 여러 기법 실험 필요.
- CNN과 같이 Inductive bias, local information을 보상하는 구조가 없어, 저SNR에서 급격히 무너짐. 따라서 향후 연구에서 CNN+Transformer(Conformer)구조 채택은 필연적.
- IQ데이터를 복소수 형태로 Embedding하여 Transformer에 집어넣은 것이 주된 내용. 그러나, 주된 Inference Time의 증가가 CMHSA 내부 Complex multiplication과 Complex correlation 때문임.
- RPO(Random Phase Offset) 기법을 도입하여, Data augmentation 효과를 연구에 적용 가능.
- Transformer 구조 도입시, Class token을 추가하고, 마지막에 학습된 Class token을 추출하여 classification할 수 있음.
- Talking heads 기법을 도입하여, 표현력을 극대화 할 수 있지만, CNN에서 이미 표현력을 높혀 놓았기에 'Over-smoothing'(토큰들의 특징이 너무 비슷해져 버림)현상 발생 가능. 따라서 모델에 적용시킨다면, 특정 임계값 이하의 연결은 끊어버리는 희소화(Sparsification) 기법 적용도 생각.
- RPE(Relative Positional Embedding) 기법을 도입하여, Conformer구조에 Positional Embedding을 명시적으로 적용시킬 수도 있음. 그러나, 앞선 CNN을 통과하며 암묵적인 상대적 위치 정보(Implicit Positional Clues)를 자연스럽게 인코딩하므로, accuracy 향상 대비 inference time 혹은 parameter의 증가가 타당한지 실험 필요. 추가로, EAA 혹은 Linear Transformer와 같이 O(n)연산 복잡도를 가진 Transformer model은 '상대적인 위치'정보 자체를 넣을 수 없음. 따라서, 현재 구상중인 Conformer 구조에는 들어갈 계획이 없음.
---
## 📝 내 요약 노트 (Zotero Notes)

## 용어

- ## 윈도우:
    
    관측하는 ‘틀’이자 ‘방식’.
    
    연속적인 시계열 데이터 중 특정 구간만 잘라서 보기 위해 사용하는 시야의 틀.
    
- ## 프레임:
    
    윈도우를 통해 잘려 나온 ‘데이터 결과물’.
    

## 통신

- ## Symbol:
    
    디지털 신호 전송의 최소 단위
    
    여러개의 비트로 이루어짐
    
- ## Intersymbol Interference(ISI):
    
    앞서 보낸 신호(심볼)가 채널의 특성 때문에 시간상으로 퍼지면서, 뒤이어 전송되는 신호를 침범하고 왜곡시키는 현상(aliasing이 본인의 신호를 연속적으로 만들면서 겹쳐지는 현상이라면, ISI는 두 개의 서로 다른 신호가 겹쳐지는 현상)
    
- ## In-phase(I), Quadrature-phase(Q)의 관계:
    
    I와 Q는 서로 직교하는 관계(pi/2만큼의 위상차만 존재하고, 나머지는 동일)이므로, inductive bias를 활용하는 것이 중요.
    
    만약 I를 통해 완벽하게 신호를 구별할 수 있다면, Q를 통해서도 완벽하게 구별할 수 있어야함.
    
    그러나, 실제로는 노이즈 영향으로 두 신호간 완벽하게 대칭적으로 이루어지지 않음.
    
    따라서 공유된 파라미터를 통해 I와 Q를 학습시키는 것은 Inductive bias 관점에서 당연함(만약 서로 별개의 파라미터를 활용하여 학습시킨다면, I 혹은 Q 각각이 자기만 지니고 있는 noise에 overfitting될 것).
    
    실제 환경에서는 완벽하게 pi/2에 대칭적으로 보이지 않기에, 공유된 파라미터와 독립적인 파라미터 비율을 조절하여 결함을 모델이 스스로 발견하고 보정하는 연구를 할 수도 있을 것.
    
- ## Sample Rate Offset(SFO):
    
    디지털 신호처리에서 기준(이상적인) 샘플링 속도와 실제 하드웨어 기기가 작동하는 샘플링 속도 간의 미세한 오차
    
- ## Center Frequency Offset(CFO):
    
    송신기와 수신기가 각각 carrier 주파수만큼 주파수를 올리거나 내릴 때, 두 발진기 사이 발생하는 미세한 주파수 불일치(중심 주파수의 미세한 오차).
    
- ## Symbol Rate Offset(SRO):
    
    송신기가 초당 1,000개의 심볼을 보낸다고 가정했을 때, 수신기의 ADC(아날로그-디지털 변환기) 클럭이 미세하게 빠르거나 느려서 초당 1,001개나 999.5개의 속도로 샘플링을 해서 생기는 오차.
    
- ## Fading:
    
    송신기와 수신기 사이에서 전파가 전달될 때, 장애물이나 반사, 이동 속도 등에 의해 수신 신호의 세기와 품질이 시간에 따라 불규칙하게 변동하는 현상.


---
## 🖋️ 조테로 하이라이트 & 캡처
> [!quote]|#5fb236
> However, the I/Q data are two consistent (both translational superposition of shaping waveforms) data with only a phase difference of π /2, according to Hilbert transform [21], so they can teach the network independently and make more sufficient learning. ([p.2](zotero://open-pdf/library/items/NXDECY6E?page=2))
> **메모:** Hilbert transform: signal을 90도(j)만큼 변환시킨 것(I, Q phase관계)
ex. cos의 hilbert 변환은 sin함수
> [!quote]|#5fb236
> The network parameters need to fit both the I and Q data, which can be seen as doubling the training data in disguise. ([p.2](zotero://open-pdf/library/items/NXDECY6E?page=2))
> **메모:** I와 Q 두 개의 데이터는 사실상 90도 관계이므로, 전체 트레이닝 가능한 데이터셋은 2배가 되는 것과 동일함
> [!quote]|#ffd400
> Moreover, we propose a data augmentation method of adding random phase offset (RPO), which is motivated by the phase offset estimation proposed in [22] and [23] using fully connection (FC) layers, where the estimated phase offsets are supervised end-to-end by the modulation types instead of the ground truth values ([p.2](zotero://open-pdf/library/items/NXDECY6E?page=2))
> **메모:** RPO(Random Phase Offset)데이터 증강 기법: 위상을 무작위로 추가하여 데이터 증강. 추가적인 파라미터를 요구하지 않음. 데이터 증강의 본질적 메커니즘 극대화

Rotational Invariance를 통해 성능 향상(phase가 돌아가도, 동일한 QAM, BPSK임을 밝혀냄 = CFO 영향 최소화)
![[AMC_Papers/images/image-4-x43-y463.png]]
> [!quote]|#ffd400
> By being connected in series with token sequence and fed into the network, the class token can encode the overall feature of a sample and be used for classification. ([p.4](zotero://open-pdf/library/items/NXDECY6E?page=4))
> **메모:** Class token: Token sequence앞에 concat하여 전역적인 정보를 학습하도록 함.
이후, classification에서 활용
> [!quote]|#5fb236
> Since the I/Q components are data with the same distribution pattern, i.e., Hilbert transform pairs, they can share the same learned parameters. ([p.4](zotero://open-pdf/library/items/NXDECY6E?page=4))
> **메모:** I와 Q 데이터는 phase 차이만 있을 뿐, 동일한 분배 패턴을 가진 데이터이므로, 동일하게 학습된 파라미터를 공유 가능함
> [!quote]|#5fb236
> In CV-TRN, the I/Q components are transmitted independently except in the MHSA, where the information about both I/Q is necessary to measure the similarity between tokens, considering that I and Q together contain amplitude and phase change information that is important for the AMR task. ([p.4](zotero://open-pdf/library/items/NXDECY6E?page=4))
> [!quote]|#ff6666
> Q(k) i , Q(qk) = (Xin_i, Xin_q  )W (k)  Q ([p.4](zotero://open-pdf/library/items/NXDECY6E?page=4))
> **메모:** CMHSA 수식1
I와 Q에 대한 Query
> [!quote]|#ff6666
> K(k) i , Kq(k) = (Xin_i, Xin_q  )W (k)  K . ([p.5](zotero://open-pdf/library/items/NXDECY6E?page=5))
> **메모:** CMHSA 수식2
I와 Q에대한 key
![[AMC_Papers/images/image-5-x31-y255.png]]
![[AMC_Papers/images/image-5-x63-y38.png]]
![[AMC_Papers/images/image-5-x317-y470.png]]
![[AMC_Papers/images/image-5-x343-y360.png]]
![[AMC_Papers/images/image-6-x64-y583.png]]
> [!quote]|#ff6666
> In the baseband transmission system, the sampling points of the shaping waveforms in different frames will be biased, which can be measured by the relative position. ([p.6](zotero://open-pdf/library/items/NXDECY6E?page=6))
> **메모:** 1. 변조 방식의 본질: 현재 signal과 직전 혹은 직후 signal의 위상과 진폭 변화임.
2. 시계열 패턴의 일반화: 만약 신호가 이동하여도(Translation shift, Time shift), RPE 방식을 통해 상대적인 거리 기반으로 Attention score를 계산한다면, 동일한 위상/진폭 변화를 동일하게 알아차릴 수 있음
![[AMC_Papers/images/image-6-x45-y338.png]]
![[AMC_Papers/images/image-6-x70-y290.png]]
![[AMC_Papers/images/image-6-x110-y191.png]]
![[AMC_Papers/images/image-6-x45-y135.png]]
![[AMC_Papers/images/image-6-x359-y465.png]]
> [!quote]|#ffd400
> The augmentation operation is through randomly generating an offset ratio 0 ≤ r ≤ 1 during training, and then, a phase transformation using r is implemented as  sPoffset(t) = s(t)e2π ri  = [i(t) + q(t)i][cos(2π r) + sin(2π r)i] = [i(t)cos(2π r) − q(t)sin(2π r)]  + [i(t)sin(2π r) + q(t)cos(2π r)]i  iPoffset(t) = i(t)cos(2π r) − q(t)sin(2π r) qPoffset(t) = i(t)sin(2π r) + q(t)cos(2π r). ([p.7](zotero://open-pdf/library/items/NXDECY6E?page=7))
> **메모:** RPO 수식
Rotational Matrix 적용
![[AMC_Papers/images/image-8-x40-y503.png]]
![[AMC_Papers/images/image-8-x68-y165.png]]
