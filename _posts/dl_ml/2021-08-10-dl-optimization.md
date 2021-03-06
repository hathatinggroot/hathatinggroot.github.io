---
title: "[DL/ML]Optimization - Important Concept"
categories:
  - DL-ML
tags:
  - DeepLearning
  - Optimization
  - Generalization
  - Underfitting
  - Overfitting
  - CrossValidation
  - BiasVarianceTradeoff
  - Bootstraipping
  - Bagging
  - Boosting
last_modified_at: 2021-08-10T00:00:00-00:00
---


## Summary ๐ค
<hr/>

"๋ชจ๋ธ์ ์ฑ๋ฅ์ด ์ข๋ค"๋ผ๋ ๊ธฐ์ค๋ค์ ์์๋ณด๊ณ  ์ด๋ป๊ฒ ํฅ์์ํฌ ์ ์๋์ง ์์๋ณธ๋ค.     
>๋จ, ์ด๋ค ๋ฐฉ๋ฒ์ด๋  test data๋ฅผ ํ์ฉํ๋ฉด cheating์์ ๋ช์ฌํ์.

<br><br/>


## Index ๐       
  * [Generalization](#Generalization)
  * [fitting(Under|Over)](#Underfitting--Overfitting)
  * [Cross validation](#cross-validation)
  * [Bias-variance tradeoff](#bias-variance-tradeoff)
  * [BootStrapping](#bootstrapping)
  * [Bagging & Boosting](#Bagging--Boosting)

<br><br/>


## Generalization  
<hr/>
Trainning Error์ Test Error์ ์ฐจ์ด๋ฅผ ๋ํ๋ด๋ ๊ฒ์ผ๋ก ์ด Gap์ ์ค์ด๋ ๊ฒ์ ๋ชฉํ๋ก ๊ฐ์ง๊ฒ ๋๋ค.   
ํ๋ จ ๋ฐ์ดํฐ๋ฅผ ํตํด ์ป์ Weight๊ฐ ์ค์  ๋ฐ์ดํฐ(test data)์์๋ ์ผ๋ง๋ ์ ์ ์ฉ๋๋์ง ๋ํ๋ธ๋ค.   

<br><br/>

   

## Underfitting & Overfitting
<hr/>
__Underfitting__  ์ด๋ ํ์ต ๋ฐ์ดํฐ์ ๋ง๋ ํ๋ผ๋ฏธํฐ๊ฐ ๋์จํ๊ฒ ํ์ต๋ ํํ๋ก์ ์ ์ ํ ํ๋ผ๋ฏธํฐ๋ก ํ๋จํ๊ธฐ ์ด๋ ค์์ง๋ค.    
__Overfitting__ ์ด๋ ํ์ต ๋ฐ์ดํฐ์ ๊ณผ๋ํ๊ฒ ์ต์ ํ๋ ๊ฒ์ผ๋ก์ ์์ ์ธ๊ธํ Generalization gap์ ์ฆ๊ฐ์ํฌ ์ ์๋ค.    

  
<br><br/>

## Cross-validation
<hr/>
K-fold Cross-validation์ด๋ผ๊ณ  ๋ถ๋ฅด๊ธฐ๋ ํ๋ค.   
๋ฐ์ดํฐ์์ ์ผ์ ํ ํฌ๊ธฐ๋ก k ๊ทธ๋ฃน์ผ๋ก ๋๋์ด 1๊ฐ์ validation set(test set์ด ์ ๋ ์๋๋ค.)๊ณผ k-1๊ฐ์ training set์ผ๋ก ๋๋์ด ํ์ต์ ํ์ฉํ๋ ๊ฒ์ด๋ค.     

์๋ฅผ ๋ค์ด 100๊ฐ์ ๋ฐ์ดํฐ ์์ 10๊ฐ์ fold๋ก ๋๋๊ณ  ๋ชจ๋ธA์ ๋ํด์๋ 1~9 fold ๋ฐ์ดํฐ์์ training set์ผ๋ก ํ์ฉํ๊ณ  10 fold ๋ฐ์ดํฐ์์ validation set์ผ๋ก ํ์ฉ, ๋ชจ๋ธ B, C์ ๋ํด์ ๊ฐ๊ฐ ๋ค๋ฅธ validation set์ ํ์ฉํด ๊ฐ๊ฐ์ ์ฑ๋ฅ์ ๋น๊ตํ์ฌ ์ ์ ํ ๋ชจ๋ธ์ ํํ๋ ๋ฐฉ์์ด๋ค.    
์ฃผ๋ก [hyperparameter](https://machinelearningmastery.com/difference-between-a-parameter-and-a-hyperparameter/)(learing rate...)์ ๊ฐ์ ๋ชจ๋ธ์ ํน์ง์ ํ๊ฐํ๊ณ  ๋น๊ตํ๊ธฐ ์ํด ์ฌ์ฉํ๋ค.    

<br><br/>

## Bias-Variance tradeoff
<hr/>
์ฃผ์ด์ง ๋ฐ์ดํฐ์ ๋ธ์ด์ฆ๊ฐ ์๋ ๊ฒฝ์ฐ Bias์ Variance๋ ๋ค์์ ๊ด๊ณ๋ก ์ธํด ๋๋ค ๋์์ ์ค์ด๋ ๋ชจ๋ธ์ ์ฐพ๋ ๊ฒ์ ํ๋ค๋ค.    

Cost = Bias^2 + Variance + Noise   
> $\begin{aligned} \mathbb{E}\left[(t-\hat{f})^{2}\right] &=\mathbb{E}\left[(t-f+f-\hat{f})^{2}\right] \\ &=\cdots \\ &=\mathbb{E}\left[\left(f-\mathbb{E}[\hat{f}]^{2}\right)^{2}\right]+\mathbb{E}\left[(\mathbb{E}[\hat{f}]-\hat{f})^{2}\right]+\mathbb{E}[\epsilon] \end{aligned}$

<br><br/>



## BootStrapping
<hr/>
ํ์ต๋ฐ์ดํฐ๊ฐ ์์ ๋ sub sampling์ ํตํด ๋ฐ์ดํฐ๋ฅผ ๋๋๋ ๊ฒ์ด๋ค.    


<br><br/>



## Bagging & Boosting
<hr/>
Bagging (Bootstrapping aggregating) : ๋ฐ์ดํฐ๋ฅผ bootstraping ํ์ฌ ์ฌ๋ฌ๊ฐ์ ๋ชจ๋ธ๋ก ๋๋ฆฝ์ ์ผ๋ก ํ์ตํ๋ ๋ฐฉ์์ด๋ค.   
Dectreteํ ์์ธก๊ฐ์ vote, ์ฐ์ ๋ฐ์ดํฐ๋ ํ๊ท ์ผ๋ก ๊ฒฐ๊ณผ๋ฅผ ๋์ถํ๋ค.    

Related : [Random Forest](https://ko.wikipedia.org/wiki/%EB%9E%9C%EB%8D%A4_%ED%8F%AC%EB%A0%88%EC%8A%A4%ED%8A%B8)

Boosting : Bagging๊ณผ ๋์ผํ๋ ๊ฐ ๋ชจ๋ธ์ด ๋๋ฆฝ์ ์ธ ํํ๊ฐ ์ด๋ Sequentialํ๊ฒ ๋ฐฐ์นํ์ฌ ์ฌ๋ฌ ๊ฐ์ weak learner ๋ฅผ ํตํด 1๊ฐ์ strong learner๋ฅผ ๋ง๋๋ ๋ฐฉ์์ด๋ค.      




<br><br/>