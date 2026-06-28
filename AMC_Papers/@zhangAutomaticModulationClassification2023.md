---
type: literature_note
citekey: zhangAutomaticModulationClassification2023
tags:
  - AMC
  - paper
  - AWN
  - LifitingScheme
  - Wavelet
  - HybridArchitecture
---
# Toward the Automatic Modulation Classification With Adaptive Wavelet Network

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> With the evolutionary development of modern communications technology, automatic modulation classiﬁcation (AMC) has played an increasing role in the complex wireless communication environment. Existing AMC schemes based on deep learning use a neural network to extract features and calculate feature maps, then feed them into fully connected layers for classiﬁcation. However, existing schemes still are insufﬁcient in utilizing feature maps. To overcome this limitation, a novel adaptive wavelet network (AWN) is proposed, which combines adaptive wavelet decomposition based on the lifting scheme and channel attention mechanism.In contrast to the previous models, the multi-level decomposition of AWN explicitly extracts the features of multiple frequency bands. The channel attention mechanism further selects the optimal frequencies from the candidate frequencies. AWN explores a novel AMC paradigm that efﬁciently integrates the inherent properties of the signal by introducing prior knowledge in the frequency domain. Simulation results demonstrate that our proposed AMC scheme outperforms the benchmark scheme and has rather low computational complexity.

- **저자:** Jiawei Zhang, Tiantian Wang, Zhixi Feng, Shuyuan Yang
- **발표 연도:** 2023
- **Zotero 바로가기:** [로컬 앱에서 열기](zotero://select/library/items/BB7ZIAF7)
- **PDF 원문 보기:** [옵시디언에서 열기]()

---
## 🧠 AMC 연구 적용 포인트

- 논문에서 제시된 Squeeze-Excitation Attention 기법 뿐만 아니라, 다른 효과적인 Linear time complexity O(N)기반 Attention 기법 활용검토
- 현재 Lifting Scheme은 frequency가 총 T+1개로 Discrete하게 끊어짐. 이를 보완하기 위해, 완전히 연속적으로 frequency를 계산할 수 있는 방법 찾기.
- 만약 Lifting Scheme을 그대로 사용한다면, CNN->Lifting Scheme(Tokenizer) -> Transformer flow 구성.
- 현재 구조와 같이, 주파수(T+1개의 토큰)간 Attention을 통해 Attention scores를 매기는 경우, SNR-Aware Attention으로 변조(수신된 신호의 예상 SNR 값을 Attention Network의 추가 입력으로 넣어줌). 이를 통해 저SNR같이 고차 주파수에서 노이즈가 가득한 경우, 고차 주파수(H)의 Attention scores를 매우 낮추는 방향으로 학습 가능.
- Multi-level Decomposition 구조에서, 주파수 대역 간 Conv1D를 통해 저주파의 진폭(Envelope)변화가 일어나는 시점과 고주파의 위상(Phase)가 튀는 시점 간의 상관관계 학습 추가가능.
- 위의 접근법은 GAP를 거치면 시간에 대한 정보가 완전히 소멸하므로, GAP 이전 Time Sequence를 인지 가능한 상태에서 적용시켜야 함. 대역폭마다 다른 시퀀스 길이(L, L/2, L/4)를 Interpolation이나 Upsampling을 통해 동일한 시간 길이로 맞춤 -> 모든 대역폭의 Feature map을 Concatenate -> PWConv1D를 통해 동일한 시간에 존재하는 여러 주파수 대역 간 비선형적인 조합 생성.
- 이후 MBCA(Multi-Band Cross-Attention)기법 도입: Query(저주파 특징 맵, L), Key and Value(고주파 특징 맵, H) 적용. Trend를 나타내는 L이 기준이 되어 노이즈가 가득한 H 중 유의미한 성분만을 뽑아냄(Noise Suppression 효과). 대신, O(N^2)연산 복잡도를 줄일 필요 있음.
-  아날로그 변조 방식 내 침묵 구간(silent period) 취약성: 모든 딥러닝 기반 모델이 공유하는 약점이기도 하나, AWN 역시 WBFM(Wideband Frequency Modulation)이나 AM-DSB와 같은 연속형 아날로그 변조 방식을 분류하는 데 어려움. 짧은 샘플 관측 윈도우(N=128) 내에 이러한 침묵 구간만이 포착될 경우, 모든 샘플 값이 0에 수렴하는 무의미한 벡터가 입력되기에, 아무리 정교한 적응형 웨이블릿 분해라 하더라도 추출할 주파수 에너지가 없으므로 신경망은 맹목적인 무작위 추측(Random guess)에 의존하게 됨. 또한 AM-SSB신호 파형이 AWGN과 유사한 특징을 가지므로, 제대로 파악하지 못하는 단점을 개선해야함.
- 고차 QAM간 구분 능력도 개선점.
---
## 📝 내 요약 노트 (Zotero Notes)

## 통신

- ## STFT(Short Time Fourier Transform):
    
    non-stationary(비정상성)의 신호에 대해 유사한 신호를 뽑아내는 수학적 도구.
    
    윈도우 크기가 짧다면, 급격히 변화하는 신호에 대응이 좋지만, 유사성을 나타내기 어려움.
    
    윈도우 크기가 길다면, 급격히 변화하는 신호에 대응이 어렵지만, 유사성을 나타내기 좋음.
    
    윈도우 크기가 무한대인 경우, FT(Fourier Transform)과 동일
    
- ## WT(Wavelet Transform):
    
    STFT와 동일점: 윈도우 단위로 신호를 해석
    
    STFT와  차별점: STFT가 하나의 윈도우 안에 하나의 주파수에 해당하는 신호만 넣을 수 있다면, WT는 하나의 윈도우 안에 수백 수만 가지의 주파수 신호를 넣을 수 있음.
    
    따라서, 신호 분해 능력이 월등히 좋음.
    
    그러나, 필요 연산량이 압도적으로 늘어남.


---
## 🖋️ 조테로 하이라이트 & 캡처
> [!quote]|#ffd400
> 1) Splitting: This step consists of splitting the input signal into two non-overlapping partitions. Generally, the input signal x is divided into even and odd components denoted as xe and xo, respectively. It can be represented as:  [xo , xe ] = Split(x ) xo [n] = x [2n + 1]  xe [n] = x [2n] ([p.3](zotero://open-pdf/library/items/YL4BILST?page=3))
> **메모:** 1. Sample 분할
x_e[n]: Even sample
x_o[n]: Odd sample

2. 인접한 샘플들은 서로 높은 상관관계(Corr)을 가지므로, 짝수 샘플의 흐름을 알면, 홀수 샘플의 흐름도 유추가능
> [!quote]|#ffd400
> 2) Predictor: Based on the correlation of the signals, a prediction operator P (·) is used to predict xo from xe . Because of the strong correlation between xo and xe , when using a good predictor P (·) to estimate xo, the difference between the two can be a good indication of high-frequency details. This process can be expressed as:  d = xo − P (xe ) (2)  where d means details and denotes the difference between xo and P (xe ). ([p.3](zotero://open-pdf/library/items/YL4BILST?page=3))
> **메모:** 1. x_e(even sample)을 prediction operator를 통해 x_o(odd sample)을 유추하는 것

2. details d가 작다면:
x_e와 x_o가 Trend에서 벗어나지 않는다는 의미로, 저주파 성분으로 이루어짐.

3. details d가 크다면:
x_e와 x_o가 급격한 변화가 발생하므로, 고주파 성분으로 이루어짐.

4. 즉, details d가 고주파 성분을 나타냄.
> [!quote]|#ffd400
> 3) Updater: The updater refers to update xe with the update operator U (·). The details d is further used in U (·) to update the even part. The updated xe is a good approximation of the low-frequency components of the original x. It can be expressed as:  c = xe + U (d ) (3)  where c is the approximation coefficient. ([p.3](zotero://open-pdf/library/items/YL4BILST?page=3))
> **메모:** 1.  전체적인 Trend(low-frequency)를 구하기 위해, c(approximation coefficient)를정의

2. x_e를 d(high-frequency)성분만큼 U(update operator)를 이용해 보정하여 c(low-frequency)를 구함.
> [!quote]|#ff6666
> However, it is lack adaptability and can not leverage datadriven learning. The fixed U (·) and P (·) can be replaced by the nonlinear fitting function of neural networks ([p.3](zotero://open-pdf/library/items/YL4BILST?page=3))
> **메모:** 1. 기존 Lifting scheme에서 고정된 P(predict operator), U(update operator)를 사용하였으나, 해당 논문에서는 P와 U를 CNN 블록으로 구성

2. CNN Block 구조:
Padding -> Conv1D(1x3) -> ReLU -> Conv1D(1x3) -> Tanh

3. CNN을 통해, P와 U를 optimal하게 학습시킴으로써 기존 Lifting scheme보다 성능 향상

4. H(high-frequency, d) 성분은 최소화 되도록(=예측을 잘 할 수 있도록), L(low-frequency, c) 성분은 원본(gnd truth)를 잘 유지하도록 손실 함수(Loss function) 구성
> [!quote]|#ffd400
> As written in [72], GAP is a special case of discrete cosine transform, and only the lowest frequency information is preserved. ([p.4](zotero://open-pdf/library/items/YL4BILST?page=4))
> **메모:** 1. GAP의 경우, Trend만 명시적으로 뽑아내는 것으로 이해할 수 있음.

2. 이것은 신호의 lowest frequency만을 뽑아내는 것과 동일

3. 나머지 영역의 frequency(higher frequency)들은 모두 삭제됨.
> [!quote]|#5fb236
> Mathematically,  r ∈ CN → r I /Q ∈ R2×N ([p.5](zotero://open-pdf/library/items/YL4BILST?page=5))
> **메모:** r: received signal
N: sequence
![[AMC_Papers/images/image-6-x72-y582.png]]
![[AMC_Papers/images/image-6-x331-y650.png]]
![[AMC_Papers/images/image-6-x214-y511.png]]
![[AMC_Papers/images/image-6-x452-y495.png]]
> [!quote]|#ff6666
> 2 × 7 kernel size to integrate the information of the I and Q channels. ([p.6](zotero://open-pdf/library/items/YL4BILST?page=6))
> [!quote]|#ff6666
> with 1 × 5 kernel size and 1 × 3 kernel size respectively. ([p.6](zotero://open-pdf/library/items/YL4BILST?page=6))
![[AMC_Papers/images/image-7-x354-y212.png]]
