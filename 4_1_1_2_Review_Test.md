# 深層学習 day３ Section１：再帰型ニューラルネットワークの概念

## 確認テスト１

RNNのネットワークには大きくわけて3つの重みがある。1つは入力から現在の中間層を定義する際にかけられる重み、1つは中間層から出力を定義する際にかけられる重みである。残り1つの重みについて説明せよ。

解答：

   中間層から中間層へ至るところの重み。前の中間層からの重み。

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

下図のy1をx・s0・s1・win・w・woutを用いて数式で表せ。※バイアスは任意の文字で定義せよ。※また中間層の出力にシグモイド関数g(x)を作用させよ。

<p align="center">
    <img src="https://github.com/ontheroad2021/RabbitChallenge/blob/main/images/4_1_1_2_Review_Test_01.png"> 
</p>

解答：
```
# 2層の総入力
u2 = np.dot(z1, W2) + b2
    
# 2層の総出力
z2 = functions.relu(u2)
```    
