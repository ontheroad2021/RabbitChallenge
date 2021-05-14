# 深層学習 day１ Section４：勾配降下法

## 確認テスト１

以下の勾配降下法に該当するソースコードを探してみよう。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\mathbf{w}^{(t+1)}&=\mathbf{w}^{(t)}-\varepsilon\nabla%20E_{n}\end{align*}"> 
</P>

 
<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{document}\color{black}\nabla{E}=\frac{\partial{E}}{\partial\mathbf{w}}=\begin{bmatrix}\frac{\partial{E}}{\partial{w_1}}\cdots\frac{\partial{E}}{\partial{w_n}}\end{bmatrix}\end{document}"> 
</P>


解答：

該当するコードは確率的勾配降下法の中から以下の行になる。

```
network[key]  -= learning_rate * grad[key]
```

```
# 勾配降下の繰り返し
for dataset in random_datasets:
    x, d = dataset['x'], dataset['d']
    z1, y = forward(network, x)
    grad = backward(x, d, z1, y)
    # パラメータに勾配適用
    for key in ('W1', 'W2', 'b1', 'b2'):
        network[key]  -= learning_rate * grad[key]

    # 誤差
    loss = functions.mean_squared_error(d, y)
    losses.append(loss)

print("##### 結果表示 #####")    
lists = range(epoch)
```
   

## 確認テスト２

深層学習にとって大切なオンライン学習を定義しなさい。

解答：

オンライン学習とは学習データが入ってくる度に都度パラメータ（重み）を更新し、学習を進めていく方法。一方、バッチ学習では一度にすべての学習データを使用してパラメータ更新を行う。最近の深層学習ではオンライン学習というのがかなり重要な要素になっている。


## 確認テスト３

以下の数式の意味を図に書いて説明せよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\mathbf{w}^{(t+1)}&=\mathbf{w}^{(t)}-\varepsilon\nabla%20E_{t}\end{align*}"> 
</P>

解答：

   ![GitHub Logo](/images/3_1_4_2_Review_Test_03.png)
