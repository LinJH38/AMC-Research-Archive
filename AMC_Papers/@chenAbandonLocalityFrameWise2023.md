---
type: literature_note
citekey: chenAbandonLocalityFrameWise2023
tags: [AMC, paper]
---
# Abandon Locality: Frame-Wise Embedding Aided Transformer for Automatic Modulation Recognition

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> Automatic modulation recognition (AMR) has been considered as an efﬁcient technique for non-cooperative communication and intelligent communication. In this work, we propose a modiﬁed transformer-based method for AMR, called frame-wise embedding aided transformer (FEA-T), aiming to extract the global correlation feature of the signal to obtain higher classiﬁcation accuracy as well as lower time cost. To enhance the global modeling capability of the transformer, we design a frame-wise embedding module (FEM) to aggregate more samples into a token in the embedding stage to generate a more efﬁcient token sequence. We also present the optimal frame length by analyzing the representation ability of each transformer layer for a better trade-off between the speed and the performance. Moreover, we design a novel dual-branch gate linear unit (DB-GLU) scheme for the feed-forward network of the transformer to reduce the model size and enhance the performance. Experimental results on RadioML2018.01A datasets demonstrate that the proposed method outperforms state-of-the-art works in terms of recognition accuracy and running speed.

- **저자:** Yantao Chen, Binhong Dong, Cuiting Liu, Wenhui Xiong, Shaoqian Li
- **발표 연도:** 2023
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/A3CFKN7H)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트

- CNN을 제거함으로써 생기는 Inductive bias, local information의 부재로 인해, 저SNR에서 정확도가 매우 낮음(노이즈 저항력의 상실). 따라서 우리 모델에서는 CNN을 삽입해야함.
- I/Q를 단순 concatenate함으로써, 회전 불변성과 위상 상관관계 학습을 전혀 하지 못함. 복소수 상관관계를 암묵적으로 재학습해야 하므로 데이터 효율성 저하됨. 따라서 우리 모델에서는 I/Q의 complex 특성을 활용하여 융합하는 CNN을 앞단에 삽입.
- 최적의 하이퍼파라미터 L=32에서 총 파라미터 수는 대략 168K~177K 수준으로 목표로 하는 15K이하에는 10배 정도의 차이가 존재함.
- DB-GLU 이식(FFN 파라미터 다이어트): Transformer 활용 시, FFN 대신 DB-GLU를 적용하여, 파라미터 수를 극소화한 상태에서도 손실된 feature map의 표현력을 증폭. 그러나, 우리 모델에서는 논문에서 나오는 순수한 MHSA(Multi-Head Self-Attention)대신 O(N)시간 복잡도의 Attention 기법 활용.

---
## 📝 내 요약 노트 (Zotero Notes)

## 용어

- ## Rank(선형대수학):
    
    행렬의 column이 만들어내는 벡터 공간에서 basis의 최대 개수이자, 그 공간의 Dimension(서로 독립적인 차원을 가지는 basis의 수).
    
- ## Low-Rank Bottleneck:
    
    S(시퀀스 길이)는 넓은데, 헤드 차원(d_p)가 너무 적어서 MHSA에서 [S,S]의 다채로운 관계를 표현하지 못하는 현상.
    
    Rank inequality:
    
    [rank(AB)<=min(rank(A),rank(B))]관계 성립.
    
    계산의 효율성을 위해, Transformer에서 일반적으로 d_p를 S보다 작게 설정한다(Q와 K [S,d_p]).
    
    이를 Rank inequality 수식에 대입하면, P(Context Attention Matrix, [S,S])의 최대 rank가 d_p로 결정된다.
    
    만약 S = 128, d_p =16이라면, [128, 128] Matrix(128 시퀀스 간의 관계)를 단 16가지 패턴으로 제한시켜 나타내야 한다(=Low-Rank Bottleneck).
    




---
## 🖋️ 조테로 하이라이트 & 캡처
> [!quote]|#ffd400
> In general, the modulated signals usually transmit bit sequences without semantic information, and each modulation symbol appears in the waveform with uniform probability. Hence, more valuable features for the AMR task should be uniformly distributed in the waveform. The extract of these features should not be within the locality bias assumption. ([p.](zotero://open-pdf/library/items/WUAU9FE8?page=))
> **메모:** 1. 통신 신호(Modulated Signals)이 자연어 데이터처럼 뚜렷한 의미론적(Semantic) 국소 정보가 없으며, 각 변조 심볼(Symbol)이 파형 전체에 걸쳐 균일한 확률분포로 존재한다는 '물리적 직괸'

2. 이에 의거하여, Inductive Bias는 사용할 필요가 없으며, Global Correlation을 추출하는 것이 AMC 성능 향상과 연산 속도 개선에 유리하다는 가설 도출

3. 따라서 Transformer의 병렬 연산 능력을 극대화하여 추론 속도를비약적으로 높히자는 결론.
> [!quote]|#ffd400
> The contributions of this study are summarized as follows. ([p.](zotero://open-pdf/library/items/WUAU9FE8?page=))
> **메모:** [contribution]
1. Inductive Bias를 극복하고 Transformer만 사용

2. 경량화

3. Inference Time 최소화
![[AMC_Papers/images/image-2-x390-y668.png]]
![[AMC_Papers/images/image-2-x431-y669.png]]
![[AMC_Papers/images/image-2-x218-y594.png]]
![[AMC_Papers/images/image-2-x102-y446.png]]
![[AMC_Papers/images/image-2-x361-y595.png]]
> [!quote]|#5fb236
> input signal r ∈ CN×1 ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** 1. N: length of signal
> [!quote]|#ffd400
> Let L and R denote the frame size and the sliding step length ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** 1. L: frame size

2. R: sliding step length
> [!quote]|#ffd400
> x(t) = [rI (tR), rI (tR + 1), . . . , rI (tR + L − 1),  rQ(tR), rQ(tR + 1), . . . , rQ(tR + L − 1)]T ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [개별 프레임 column vector]
1. tR: 시작점, t(현재 프레임의 순번: 0번째, 1번째 ...), R(보폭), tR(해당 t번째 프레임이 전체 시퀀스 길이의 어디서부터 시작하는지 나타냄)

2. +1씩: 시퀀스를 한 칸씩 이동 시킴

3. L-1: 끝점(총 길이=L)

4. 차원: 2L(I와 Q를 concatenate) x 1(column vector)
> [!quote]|#ffd400
> X = [x(0), x(1), . . . , x(F −1)]T , ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [Input feature]
1. 개별 column vector x를 concatenate

2. 차원: F(전체 프레임 길이) x 2L(개별 프레임 column vector 크기)
> [!quote]|#ffd400
> F = (N − L)/R + 1 ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [Sliding Window 수식]
1. N: 전체 시퀀스 길이(ex, 128)

2. L: 프레임 길이(ex, 16칸)

3. R: 슬라이딩 윈도우(ex, 8칸)

4. +1: 첫번째 프레임을 더해준 것

5. N-L: 남아있는 이동 가능한 칸 수(ex, 128-16=112칸)

6. (N-L)/R: 남아있는 칸 수를 슬라이딩 윈도우 칸 수만큼 이동시키면서 프레임을 추가로 찍어냄(ex, 112/8 = 14: 프레임 수)

7. F: 프레임의 갯수(ex, 14(슬라이딩 윈도우 이동시키며 찍어낸 프레임 수)+1(첫번째 프레임) = 15개)
> [!quote]|#ff6666
> the learnable position bias Wpos ∈ R(F +1)×2L for position embedding ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [Positional Embedding]
1.Learnable position bias Matrix를 사용한 Absolute positional embedding 방식

------> 통신신호에서 이러한 APE를 왜 사용했을까? 트레이드오프를 알아야함. 그리고 이게 물리적으로 의미가 있을까? RPE 방식이 특징 추출에 더 우수할 것 같은데, 그냥 단순하게 진짜 Transformation 연산만을 위한 구조이기 때문에 ape인가?
> [!quote]|#ff6666
> X0 = [xcls; XWe] + Wpos. ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [최종 input token sequence]
> [!quote]|#ffd400
> For the MHSA block, we incorporate the talking-head attention [15] as the implementation scheme. ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [MHSA Block]
1. O(N^2) 연산 복잡도 Attention 기법 활용

2. talking-head 기법 활용: head가 뽑아내는 특징 간 융합 높힘
> [!quote]|#ffd400
> To compress the model size for the lightweight requirement of the AMR task, we propose a practical DB-GLU scheme to replace the traditional MLP scheme in the FFN ([p.2](zotero://open-pdf/library/items/WUAU9FE8?page=2))
> **메모:** [Feed Forward Network]
1. 기존의 MLP 방식 대신 연산량을 낮추기 위한 DB-GLU기법 활용

> [!quote]|#ffd400
> (GLU — Gated Linear Units) ([p.328](zotero://open-pdf/library/items/WUAU9FE8?page=328))
> **메모:** [GLU]
1. 본래 FFN에서 activation function(ReLU, GeLU 등)을 대체하여 표현력을 높이기 위한 방법
2. 비선형성 표현력이 높아지는 대신 연산량 증가 (Trade-off)
3. d'_ff 차원을 2/3으로 줄여 증가한 매개변수·계산량을 원래 수준으로 맞출 수 있음
4. 수식: W_fc1(W_fc1·X_l ⊗ g(W_fc2·X_l))

> [!quote]|#ffd400
> (DB-GLU) ([p.328](zotero://open-pdf/library/items/WUAU9FE8?page=328))
> **메모:** [DB-GLU]
1. GLU를 개선하여 더 높은 FFN 표현력 확보
2. W(linear projection) 차원 d_f = 4L (MLP 8L의 절반) → MLP 대비 (1/2)² = 25% parameters
3. 낮은 FLOPs와 parameters 유지

> [!quote]|#ffd400
> (전체 구조) ([p.328](zotero://open-pdf/library/items/WUAU9FE8?page=328))
> **메모:** [전체 구조]
1. CNN 앞단 제거 → 파라미터 획기적 감소 (=Abandon locality, 대신 저SNR 급격한 성능 하락)
2. FEM으로 Transformer 입력 token sequence 수 제한 → 연산 복잡도 감소
3. FFN을 MLP 대신 DB-GLU → 표현력 극대화 + 파라미터 감소
4. 순수 MHSA로도 낮은 parameters, FLOPs, Inference time 달성

> [!quote]|#ffd400
> (FEM module) ([p.328](zotero://open-pdf/library/items/WUAU9FE8?page=328))
> **메모:** [FEM module]
1. input signal r → x sequence 생성
2. Framing → X tensor 변환
3. Linear matrix 통과 + class token concatenation
4. Absolute Positional Embedding 적용
5. 최종 input token X_0 [F+1, 2L]: F+1(프레임+클래스 토큰), 2L(I/Q concatenate)
6. FEM으로 Encoder 입력 token sequence를 낮게 유지 → MHSA FLOPs 감소

> [!quote]|#ffd400
> (Received signal) ([p.328](zotero://open-pdf/library/items/WUAU9FE8?page=328))
> **메모:** [Received signal 수식]
1. s(t): transmission symbol (송신 신호)
2. m: modulation 종류
3. F: modulator
4. h(t): impulse response
5. n: noise
6. AMC: s를 통해 m을 유추

> [!quote]|#ff6666
> (MHSA dot product) ([p.329](zotero://open-pdf/library/items/WUAU9FE8?page=329))
> **메모:** [MHSA 상세]
1. P_i(Dot product) = Q·K/(d_p)^½, [F+1, F+1]
2. P̃_i(context attention matrix): W_t(head-wise linear mixing)로 talking heads 구현
3. X_i^l: i번째 헤드 feature vector, X_{l-1}(이전 layer 입력), W^i_v(value matrix)
4. softmax(p_i)로 각 토큰이 서로 참조하는 확률값으로 변환
5. i번째 헤드 feature vector가 Attention 비율대로 V값 취함, 사이즈: [F+1, d_p]
![[AMC_Papers/images/image-3-x86-y563.png]]
> [!quote]|#ff6666
> Finally, all of the heads X(i)  l ∈ R(F +1)×dp are  concatenated in the second dimension, and a linear projection Wo ∈ Rhdp×2L is applied. ([p.3](zotero://open-pdf/library/items/WUAU9FE8?page=3))
> **메모:** 1. 각 헤드의 feature maps을 concatenate 시키고 [F+1, h*d_p]

2. 이를 linear projection W_o에 적용

3. 최종 output 사이즈: [F+1, 2L]
![[AMC_Papers/images/image-3-x44-y323.png]]
> [!quote]|#5fb236
> 36L2 + 16L + h2 = O(L2) ([p.3](zotero://open-pdf/library/items/WUAU9FE8?page=3))
> **메모:** [Computational Complexity]
1. L(frame length)의 제곱에 비례
> [!quote]|#5fb236
> O(LF 2) ([p.3](zotero://open-pdf/library/items/WUAU9FE8?page=3))
> **메모:** [Computational Complexity]
1. MHSA은 F(#frame)의 제곱에 비례

2. L과 F는 반비례하므로, 최적점을 찾아야함.

> [!quote]|#ff6666
> (DB-GLU 수식) ([p.329](zotero://open-pdf/library/items/WUAU9FE8?page=329))
> **메모:** [DB-GLU 수식]
1. 표현력 극대화를 위한 새로운 GLU 구조
2. W 차원 d_f = 2L (MLP 4L의 절반) → MLP 대비 25% parameters

> [!quote]|#ff6666
> (W_Q, W_K) ([p.329](zotero://open-pdf/library/items/WUAU9FE8?page=329))
> **메모:**
1. W_Q: 각 head linear projection [2L, d_p(=2L/h)] concatenation → [2L, 2L]
2. W_K도 동일

> [!quote]|#ff6666
> (Context Attention / Low-Rank) ([p.329](zotero://open-pdf/library/items/WUAU9FE8?page=329))
> **메모:** [Context Attention scores]
1. talking heads: 기존 MHSA에서 P̃_i는 d_p 차원에 갇힘 (=Low-Rank bottleneck)
2. W_t가 이상적으로 학습되면 P̃_i ≈ W_Q·W_K^T 내적과 동일
3. W_Q·W_K^T Rank = 2L로 증가
4. Rank(P̃_i) = min(Rank(X_{l-1}), Rank(W_Q·W_K)) = min(F+1, 2L)
5. F+1 ≤ 2L이면 Low-Rank bottleneck 회피 → L_opt 도출 가능

> [!quote]|#5fb236
> (L_opt) ([p.329](zotero://open-pdf/library/items/WUAU9FE8?page=329))
> **메모:** [L_opt]
1. Row-rank bottleneck 회피: F+1 ≤ 2L
2. F = (N-L)/R + 1에 대입하여 L_opt 도출
![[AMC_Papers/images/image-3-x336-y637.png]]
![[AMC_Papers/images/image-3-x320-y519.png]]
![[AMC_Papers/images/image-3-x392-y303.png]]
