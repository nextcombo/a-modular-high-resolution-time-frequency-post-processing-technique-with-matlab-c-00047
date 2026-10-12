# A Modular High-Resolution Time-Frequency Post-Processing Technique [with MATLAB Code]

Abstract: In this letter, based on the variational model, we propose a new time-frequency post-processing technique to approximate an ideal time-frequency representation. Our method has the advantage of being modular, making it "plug and play" and independent of the performance of specific time-frequency analysis tools. Therefore, it can be easily extended to fractional Fourier domain and linear regularization domain. Furthermore, high resolution is its advantage, depending on the specific instantaneous frequency estimation method. We reveal the relationship between instantaneous frequency estimation and reassignment methods. The effectiveness of the method is verified through simulations with synthetic signals and real world signals.
Index Terms - Time-frequency representation, modularity, high resolution, redistribution
I. Introduction
Time-frequency representation (TFR) is an effective tool for describing the time-frequency characteristics of signals [1]. Therefore, obtaining high TF resolution and clear results is very important. However, traditional methods such as Short Time Fourier Transform (STFT), Continuous Wavelet Transform (CWT), S transform, chirplet transform, etc., cannot achieve ideal results. Thus, many post-processing tools for TFA have been developed to approximate the ideal TFR. For example, reassignment method (RM) [6] rearranges the TF coefficients to appropriate positions on a two-dimensional (2D) TF plane to improve TF resolution. Unfortunately, due to the reorganization on the 2D plane, it destroys the ability to reconstruct the signal. Recently, Synchronous Compression Transform (SST) [7] was proposed as a special RM that only reorganizes on the frequency or scale axis. Therefore, SST can recover the signal, making it popular. Although SST yields compact TF results, there is an energy diffusion problem that makes the TF plane appear blurry. This is unfavorable for analyzing non-stationary signals. Therefore, many improved methods have been proposed to enhance TF concentration and obtain high-resolution TFR. Overall, there are two main improvements. One option is to use a TFR with better performance instead of STFT or CWT. For example, using adaptive CWT [8], adaptive STFT [9], and adaptive S transform [10] to replace the original TFR. Another alternative is to perform a second-order or higher-order Taylor expansion of the signal to generate more accurate estimates of the instantaneous frequency (IF), such as second-order SST [11] and higher-order SST [12]. Despite the improvement in TF resolution, the computational complexity is its disadvantage. Recently, to achieve ideal TFR, a new post-processing technique called Synchronous Extraction Transform (SET) [13] was proposed, which only extracts TF coefficients near the IF and discards the rest. This leads to SET sacrificing the accuracy of the reconstructed signal. Following SET's inspiration, Local Maximal Synchronous Extraction Transform (LMSST) [14] was proposed. Its significant contribution is the introduction of a new reassignment operator, and the mid-band estimate does not rely on specific TFR. In this paper, we propose a modular high-resolution TF post-processing technique based on a variational model, which can achieve ideal TF post-processing. The results of our method are not limited by TFR performance and can be easily extended to fractional Fourier domain [15], [16], and linear regular domain [17], just by replacing TFA tools. Moreover, we reveal the relationship between the reassignment operator and IF estimation. The rest of the letter is organized as follows: Section 2 briefly reviews the theory of STFT and SST. Section 3 introduces the new TF post-processing technique. Numerical validation is presented in Section 4. Finally, conclusions are presented in Section 5.
II. Preparation
For signals s ∈ L2(R) and even-windowed g ∈ L2(R), the STFT is defined as:
\n        \n  
The signal s(t) can be reconstructed by the following equation:
\n        \n  
If there exists a sufficiently small number ε, satisfying |A^T(t)|<ε and |Total weight φ(t)|<ε, then the STFT of signal s(t)= A(t)ej(t) can be represented as:
\n        \n  
Where ω_g(ω) is the Fourier transform of g(t). Then, the spectrum of STFT is obtained in the following way:
\n        \n  
This spectrum is symmetric about IF φ(t), and its coefficients are gathered around φ(t). From formula (4), it is clear that the performance of STFT depends on g(ω). The ideal TFR we want to achieve for the signal s(t)= A(t)ej(t) is:
\n        \n  
However, it is impossible to achieve the ideal TFR with the STFT. It requires g(t)=1, which contradicts the condition of the window. To approximate the ideal TFR while maintaining the ability to reconstruct the signal, the SST is proposed, defined as:
\n        \n  
Where, ω(t, ω) is the estimated IF. The original signal s(t) can be restored by the following equation:
\n        \n  
III. Method
In [7], the adaptive TF decomposition is modeled as a variational problem, seeking to minimize:
\n        \n  
Where F(t, ω)∈L2(R2) . The paper [7] points out that the solution of the variational problem is the result of SST, i.e., for example, F(t, ω) = T(t, ω), let ω=ω . Based on short-time Fourier transform, the performance of SST is limited by the estimated IF.
However, the results of formula (9) are not very effective, leading to trailing in the TF plane. In many studies, V(t, ω) is replaced by other better TFA tools to improve SST performance, but we believe this is not the most effective method. To enhance the quality of TFR, the variational model in formula (8) is improved to
\n        \n  
п  
The purpose of this model is to find F(t, ω) that not only approximates the ideal TFR but also allows signal reconstruction. The first part of the model serves to maintain the reconstruction capability, while the second part is used to approximate the ideal TFR. However, the model in (10) is difficult to solve, so additional constraints need to be added to simplify the model.
Simplified 1: For TFR, if the redistribution only occurs on the frequency axis, the ability to restore signals is still retained in the redistribution results. Therefore, if the redistribution is limited to the frequency direction, the model in (10) is simplified as follows:
\n        \n  
Then, we consider multi-component signals   whose ideal TFR is  .
\n        \n  
Short-time Fourier Transform of signal s(t)
\n        \n  
From formulas (12) and (13), it is evident that to approximate the ideal TFR using STFT results, only the coefficients of the STFT need to be reassigned to the signal sk(t)'s IF Δk(t) = ωk(t, ω). Substituting (13) into (14), we obtain:
\n        \n  
This conclusion is easily proven, and we will not discuss it here. Therefore, (14) can be rephrased as  .
\n        \n  
Compared with formula (12) and formula (16), the new redistribution operator realizes the ideal TFR. In addition, we will prove that the new redistribution operator is reversible.
\n        \n  
Therefore, the signal can be reconstructed in the following way:
\n        \n  
From the formulas (12) and (16), it is known that to approximate T(t, ω) to ITFA(t, ω), only ωk(t, ω) needs to be close to k(t). Therefore, we can simplify the model in (11) again.
Simplification 2: Set ω = ω, the model in (11) can be further simplified to
\n        \n  
Therefore, the performance of T(t, ω) depends on the estimation result of the intermediate frequency estimate ωk(t, ω). This also determines whether T(t, τ) can eliminate energy diffusion on the TF plane. Therefore, the key to our proposed method lies in estimating IF. There are many advanced methods for IF estimation, such as Ridge Extraction Algorithm [14]. Essentially, our method is to compress the TF coefficients to IF instead of compressing them near IF like SST does. Figure 1 clearly shows how coefficients are assigned to several post-processing tools. SET only extracts TF coefficients at the estimated IF, and LMSST compresses coefficients to their maximum value within certain frequency intervals. Finally, we give a modular high-resolution TF post-processing technique. For any TFR G(t, ω), assume the signal is reconstructed by the following equation:
\n        \n  
where ρ is the reconstruction factor, which can be either digital or function-based. This depends on the specific TFR used. For example, in STFT, ρ is 1 2πg(0) .
The post-processing technique based on G(t, ω) is defined as:
\n        \n  
Reconstructing the original signal from TG(t, t) can be realized by the following way:
\n        \n  
\n        \n  
Figure 1: The way to assign coefficients to several post-processing tools.
Our approach is known for two reasons: (1) STFT V(t, ω) can be replaced by any TFA tool G(t, ω), such as short-time fractional Fourier transforms, adaptive STFT, S transform, and chirplet transforms. (2) The IF estimation value ωk(t, ω) can be replaced by any estimation method, which directly affects the performance of TG(t, ω). The combination of G(t, ω) and ωk(t, ω) yields many interesting results, but fundamentally there is no difference. In this letter, a simple and effective estimation method is proposed, its advantage is that it does not require any prior information about the signal components. The local maxima of TFR G(t, ω) are considered as the estimate of IF, i.e.,
\n        \n  
where arglmax ω| G(t, ω)| represents a set of local maximum points. However, due to interference, the number of estimated IFs through formula (23) may exceed the actual number of signal components. Therefore, we can perform a simple filter on G(t, ω) to solve this problem.  
\n        \n  
where γ is used as the filter.  
IV. Digital Verification  
In this section, our proposed method is compared with STFT and other post-processing tools, such as RM, SST, SET, and LMSST, in terms of synthetic and real world data.  
A. Multicomponent signals with obvious FM-AM characteristics  
Multicomponent signals with different FM-AM characteristics are defined as follows:  
\n        \n  
with a sampling frequency of 128Hz and a time duration of 1s.  
\n        \n  
Figure 2: Experimental results of multicomponent signals.  
The results of TFR are shown in Figure 2, indicating that our method achieves the best results. The results of STFT suffer from the poor resolution of TF, while the results of SST and SET show severe tailing. The results of LMSST are distorted at places where frequencies change rapidly. Although RM is relatively effective compared to other post-processing methods, it is reversible.
B. Multi-component signals with frequency division and intermediate frequency
In this section, we consider a multi-component signal with cross-intermediate frequency to verify the effectiveness of our method. The signal is modeled as  .
\n        \n  
The sampling frequency is 210 Hz, and the signal duration is 1 second. To demonstrate modular characteristics, we employed the IF estimation method described in [18] and [19]. Our method effectively addresses the mid-band crosstalk issue, attributed to a good mid-band estimation. Additionally, the TF results of our proposed method can be considered as trajectories of IF. Here, the relationship between IF estimation and TF reordering can also be observed. It can be concluded that the reordering results can be used for estimating IF, and the estimated IF can then be used to reallocate TF coefficients. Therefore, formula (23) can be replaced by an alternative method for IF estimation suitable for certain complex tasks.
\n        \n  
Figure 3: Experimental results of frequency-divided and intermediate-frequency signals.
C. Gravitational wave signals
To further validate the performance of our method, we applied it to gravitational wave signals, as detailed in [12]. The results of TFR are shown in Figure 4. Compared to other methods, our method and LMSST can obtain clearer TF results. However, minor frequency variations are easily overlooked by LMSST. For unknown signals, any change is worthy of attention. Our method can capture any slight changes on the TF plane. For noisy signals, interference can be filtered by adjusting the value of γ in (24) to reduce noise impact. Additionally, LMSST results exhibit ghosting and IF fast shifting within intervals t ∈ [0.43, 0.45]. Therefore, our method has potential applications in many interesting fields.
\n        \n  
Figure 4: Experimental results of gravitational wave signals.
V. Conclusions
In this letter, a new TFA technique is proposed to achieve an ideal TFR. We establish a variational model and obtain an adaptive TF decomposition. After simplifying the model, we derive the relationship between IF estimation and the ideal TFR, and clarify the relationship between IF estimation and redistribution. Future work should be to extend our technology to time-scale planes. It is also interesting to improve the quality of TFR using better IF estimation algorithms instead of the methods proposed in this paper.

## Images

![A modular high-resolution time-frequency post-processing technique [with MATLAB code]](cover.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
