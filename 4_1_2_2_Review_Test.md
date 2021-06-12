# 深層学習 day３ Section２：ＬＳＴＭ

## 確認テスト１

シグモイド関数を微分した時、入力値が0の時に最大値をとる。その値として正しいものを選択肢から選べ。

1. ０.１５  
2. ０.２５  
3. ０.３５  
4. ０.４５

解答：

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}f(x)&=0.5\times(1-0.5)\\&=0.25\end{align*}"> 
</p>
   

## 確認テスト２

連鎖率の原理を使い、dz/dx を求めよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}z&=t^2\\t&=x+y\\\end{align*}"> 
</p>

解答：

<p align="center">
    <img src="https://github.com/ontheroad2021/RabbitChallenge/blob/main/images/3_2_1_2_Review_Test_01.png"> 
</p>



## 確認テスト３

下図の <img src="https://latex.codecogs.com/svg.latex?\begin{align*}y_1\end{align*}"> を <img src="https://latex.codecogs.com/svg.latex?\begin{align*}x%20\cdot%20s_0%20\cdot%20s_1%20\cdot%20w_{in}%20\cdot%20w%20\cdot%20w_{out}\end{align*}"> を用いて数式で表せ。※バイアスは任意の文字で定義せよ。※また中間層の出力にシグモイド関数g(x)を作用させよ。

<p align="center">
    <img src="https://github.com/ontheroad2021/RabbitChallenge/blob/main/images/4_1_1_2_Review_Test_01.png"> 
</p>

解答：

<p align="center">
   <img src="https://latex.codecogs.com/svg.latex?\begin{align*}y_{1}&=g(w_{out}\cdot%20z_{1}+c)\\z_{1}&=f(w_{in}\cdot%20x_{1}+w\cdot%20z_{0}+b)\end{align*}"> 
</p>
