---
title: "[DL/ML]CNN - Intro"
categories:
  - DL-ML
tags:
  - DeepLearning
  - CNN
  - Convolution
  - ConvolutionNeuralNetwork
  - Stride
  - Padding
  - 1x1Convolution
last_modified_at: 2021-08-11T00:00:00-00:00
---


## Summary ๐ค
<hr/>
CNN(Convolution Neural Network)์ ์ผ์ ํ ํฌ๊ธฐ์ ํ๋ผ๋ฏธํฐ(filter, kernel)๋ฅผ ์ฎ๊ฒจ๊ฐ๋ฉฐ ๋์ฅ์ ์ฐ๋ฏ์ด ์ฎ๊ฒจ๊ฐ๋ฉฐ ํฉ์ฑ๊ณฑ(Convolution)ํ๋ ํํ์ ๋ด๋ด ๋คํธ์ํฌ๋ค. 

> ์ต๊ทผ์ ๋ํฅ์ ๋ ์ด์ด๋ฅผ ์ฆ๊ฐ์ํค๊ณ  ํ๋ผ๋ฏธํฐ๋ฅผ ์ค์ด๋ ๊ฒ์ด๋ค.     


<br><br/>


## Index ๐       
  * [Channel](#channel)
  * [Stride](#Stride)
  * [Padding](#Padding)
  * [Layer(Convolution, pooling, fully connected)](#layerConvolution-pooling-fully-connected)
  * [Accumualte the number of parameters](#accumualte-the-number-of-parameters)
  * [1x1Convolution](#1x1-Convolution)
  
<br><br/>


## Channel  
<hr/>

Channel์ด๋ ์ด๋ฏธ์ง์ ํ ํฝ์์ ๊ตฌ์ฑํ๋ ๋ฉํ ์ ๋ณด์ ์ฐจ์์ด๋ผ๊ณ  ํ  ์ ์๋ค.   
์๋ฅผ ๋ค์ด 100(๋์ด)x80(๋๋น) ํฝ์์ ์ปฌ๋ฌ ์ด๋ฏธ์ง๋ผ๋ฉด ์ฑ๋์ 3์ด ๋์ด ๋ฐ์ดํฐ์ shape๋ (3, 100, 80) ์ด ๋  ๊ฒ์ด๋ค.     
๋ง์ฝ ํ๋ฐฑ ์ฌ์ง์ด๋ผ๋ฉด (2, 100, 80)์ด ๋  ๊ฒ์ด๋ค.


<br><br/>

   

## Stride  
<hr/>

Stride๋ kernel ์ด ์ด๋ํ๋ ๊ฐ๊ฒฉ์ ์๋ฏธํ๋ค. 

<br><br/>

   

## Padding  
<hr/>

kernel์ ์ด๋ฏธ์ง์ ๋งจ์ฒ์๋ถํฐ ๋ชจ๋ ์ค์บํ๊ฒ ํ๋ ๋ฑ์ ํน์  ๋ชฉ์ ์ด ์์๋ ์ด๋ฏธ์ง ์ธ๋ถ์ ์์์ ๊ฐ(0)์ ๋ฃ์ด kernel์ด ์ค์บํ๋ ๋ฒ์๋ฅผ ์กฐ์ ํ  ์ ์๋ค.

<br><br/>
   



## Layer(Convolution, pooling, fully connected)  
<hr/>

* Convolution Layer : ํ๋ ๋๋ ์ฌ๋ฌ๊ฐ์ ํํฐ(kernel)๋ก ์ด๋ฃจ์ด์ง ๋ ์ด์ด์ด๋ค. ํํฐ์ ๊ฐฏ์๋งํผ์ ์ฑ๋์ด ๋ง๋ค์ด์ง๋ค.(Feature Map||Activation Map)
* Pooling Layer
  * Max pooling : ํน์  ์์ญ์์ ๊ฐ์ฅ ํฐ๊ฐ๋ง ์ทจํ๋ค.
  * Down sampling : ์๋์ ์ผ๋ก ์ด๋ฏธ์ง๋ฅผ ์ค์ฌ์ ๊ฐ์ ์ฌ์ด์ฆ์ kernel์ด ์ฐ์ฐ๋๋ฉด ์ข๋ ์ถ์์ ์ธ (์ค๊ณฝ์์ ํน์  ์ฌ๋ฌผ์ ์๋ฏธ๋ฅผ ๋ด๋ ํฌ๊ธฐ์์ ์ฐ์ฐ) ๋ฐ์ดํฐ๋ฅผ ํ์ตํ  ์ ์๊ฒ ๋๋ค.
* Fully connected : MLP๊ฐ๋๊ณผ ์ ์ฌํ๋ฉฐ ๋ถ๋ฅ๋ฅผ ์ํํ๋ค.



<br><br/>



## Accumualte the number of parameters  
<hr/>

CNN์ด ์ ์ฐจ ์งํฅํ๋ ๋ฐ๋ ํ๋ผ๋ฏธํฐ๋ฅผ ์ค์ด๊ณ  ๋ ์ด์ด๋ฅผ ๋๋ฆฌ๋ ๊ฒ์ ์๋ค๊ณ  ์์ ์ธ๊ธํ ๋ฐ ์๋ค. 

ํ๋ผ๋ฏธํฐ์ ๊ฐฏ์๋ ํํฐ์ฌ์ด์ฆ x ์ฑ๋์ x ํํฐ์(์ถ๋ ฅ ์ฑ๋ ์)๋ก ๊ตฌํ  ์ ์๋ค.


<br><br/>



## 1x1Convolution
<hr/>

1x1 ํฌ๊ธฐ์ ํํฐ๋ฅผ ์ฌ๋ฌ๊ฐ Convolution ํจ์ผ๋ก์จ ์ฑ๋ Dimension์ ๊ฐ์์ํฌ ์ ์๋ค. (์๋ ฅ ์ฑ๋์ > ํํฐ์ ๊ฐฏ์)      
๋ฐ๋ผ์ ํ๋ผ๋ฏธํฐ์ ๊ฐฏ์๋ฅผ ์ค์ด๊ธฐ ์ํด ์ฌ์ฉ๋๋ค.   


<br><br/>


## Refrence   
<hr/>

* https://89douner.tistory.com/57