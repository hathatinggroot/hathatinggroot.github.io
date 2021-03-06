---
title: "[DL/ML]Regularization"
categories:
  - DL-ML
tags:
  - DeepLearning
  - Regularization
  - EalryStopping
  - ParameterNormPenalty
  - DataArgumentation
  - NoiseRobustness
  - LabelSmoothing
  - Dropout
  - BatchNormalization
last_modified_at: 2021-08-10T00:00:00-00:00
---


## Summary ๐ค
<hr/>
Generalization์ ๋์ด๊ธฐ ์ํด ํ์ต์ ๋ฐฉํดํ๋ ๋ฐฉ๋ฒ์ด๋ค. ๋ค์ ๋งํด test set์์ ์ ๋์ํ๊ฒ ํ๊ธฐ ์ํ ๋ฐฉ๋ฒ์ด๋ค.

<br><br/>


## Index ๐       
  * [Early Stopping](#early-stopping)
  * [Parameter Norm Penalty](#parameter-norm-penalty)
  * [Data argumentation](#data-argumentation)
  * [Noise robustness](#noise-robustness)
  * [Label smoothing](#label-smoothing)
  * [Dropout](#Dropout)
  * [Batch normalization](#batch-normalization)

<br/>


## Early Stopping
<hr/>

์ถ๊ฐ์ ์ธ Validation Data๋ฅผ ๊ตฌ์ฑํ๊ณ , Training Error์ Validation Error์ ์ฐจ์ด๊ฐ ์ฆ๊ฐํ  ๋ ํ์ต์ ๋ฉ์ถ๋ ๋ฐฉ๋ฒ์ด๋ค.

<br><br/>

## Parameter Norm Penalty
<hr/>

$$
\begin{aligned}
&\text { total } \operatorname{cost}=\operatorname{loss}(\mathcal{D} ; W)+\frac{\alpha}{2}\|W\|_{2}^{2}
\end{aligned}
$$

Weight Parameter์ ํฌ๊ธฐ(์ ๋๊ฐ)๋ฅผ ์ ๊ทํํ์ฌ ์๊ฒ ๋ง๋๋ ๊ฒ์ด๋ค.    
๋ถ๋๋ฌ์ด ํจ์๊ฐ Generalization ์ฑ๋ฅ์ด ๋์ ๊ฒ์ด๋ผ๋ ๊ฐ์ ์์ ์ถ๋ฐํ๋ค.

<br><br/>


## Data argumentation
<hr/>

๋ฐ์ดํฐ๊ฐ ๋ง์ ์๋ก ์ฑ๋ฅ์ด ๋์์ง๋ค. ๋จ, ๋ฐ์ดํฐ๊ฐ ํ์ ์ ์ธ ๊ฒฝ์ฐ์ Label์ด ๋ณํ์ง ์๋ ์ ์์ ๋ฐ์ดํฐ๋ฅผ ๋ณํํ์ฌ ๋ฐ์ดํฐ ์์ ์ฆ๊ฐ์ํฌ ์ ์๋ค.

<br><br/>


## Noise Robustness
<hr/>

์๋ ฅ์ด๋ Weight์ Noise๋ฅผ ์ค๊ฐ์ ์ง์์ ์ผ๋ก ๋ฃ์ด์ฃผ๋ฉด ๋ ํ์ต๋ฅ ์ด ๋์์ง ์ ์๋ค. (์ด์ ๋ ์์ง ๋ชจ๋ฆ)

<br><br/>


## Label smoothing
<hr/>

* Mixup : ๋๊ฐ์ ์ด๋ฏธ์ง๋ฅผ ์๊ณ  label๋ ์๋๋ค.
* Cutout : ์ด๋ฏธ์ง์ ์ผ์  ์์ญ์ ๋บ๋ค.
* CutMix : ํน์  ์์ญ์ ์๋ผ ๋ค๋ฅธ ์ด๋ฏธ์ง๋ฅผ ๋ฃ๋๋ค.

<br><br/>


## Dropout
<hr/>

weight์ ์ผ๋ถ ํ๋ผ๋ฏธํฐ๋ฅผ 0์ผ๋ก ์ด๊ธฐํ ํ์ฌ ํน์  feature์ ๊ตญํ๋์ง ์๋๋ก ํ๋ค. 


<br><br/>



## Batch Normalization
<hr/>

$$
\begin{aligned}
\mu_{B} &=\frac{1}{m} \sum_{i=1}^{m} x_{i} \\
\sigma_{B}^{2} &=\frac{1}{m} \sum_{i=1}^{m}\left(x_{i}-\mu_{B}\right)^{2} \\
\hat{x}_{i} &=\frac{x_{i}-\mu_{B}}{\sqrt{\sigma_{B}^{2}+\epsilon}}
\end{aligned}
$$

 layer์ weight ํ๋ผ๋ฏธํฐ๋ฅผ ์ ๊ทํํ๋ค. (๋ผ๋์ด ๋ง์ผ๋ ๋๋ถ๋ถ์ ๊ฒฝ์ฐ์ ์ฑ๋ฅ์ด ํฅ์๋๋ค.)

<br><br/>