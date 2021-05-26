


# 深層学習 day２ Section１：勾配消失問題

## 確認テスト１

連鎖率の原理を使い、dz/dx を求めよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}z&=t^2\\t&=x+y\\\end{align*}"> 
</p>

解答：

<p align="center">
    <img src="https://github.com/ontheroad2021/RabbitChallenge/blob/main/images/3_2_1_2_Review_Test_01.png"> 
</p>


## 確認テスト２

シグモイド関数を微分した時、入力値が０の時に最大値をとる。その値として正しいものを選択肢から選べ。

<p align="center">(1) 0.15</p>
<p align="center">(2) 0.25</p>
<p align="center">(3) 0.35</p>
<p align="center">(4) 0.45</p>

以下のそれぞれに該当するソースコードを探せ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\end{align*}"> 
</p>

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\frac{\partial{\mathbf{y}}}{\partial{\mathbf{u}}}\end{align*}"> 
</p>

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\frac{\partial{\mathbf{y}}}{\partial{\mathbf{u}}}\frac{\partial{\mathbf{u}}}{\partial{w_{ji}^{(2)}}}\end{align*} ">
</p>

解答：

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\end{align*}"> 
</p>

```
delta2 = functions.d_mean_squared_error(d, y)
```

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\frac{\partial{\mathbf{y}}}{\partial{\mathbf{u}}}\end{align*}"> 
</p>

```
delta1 = np.dot(delta2, W2.T) * functions.d_sigmoid(z1)
```

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\frac{\partial{E}}{\partial{\mathbf{y}}}\frac{\partial{\mathbf{y}}}{\partial{\mathbf{u}}}\frac{\partial{\mathbf{u}}}{\partial{w_{ji}^{(2)}}}\end{align*} ">
</p>

```
grad['W1'] = np.dot(x.T, delta1)
```

いずれも以下の誤差逆伝播のコードからの抜粋になります。
```
# 誤差逆伝播
def backward(x, d, z1, y):
    # print("\n##### 誤差逆伝播開始 #####")    

    grad = {}
    
    W1, W2 = network['W1'], network['W2']
    b1, b2 = network['b1'], network['b2']

    # 出力層でのデルタ
    delta2 = functions.d_mean_squared_error(d, y)
    # b2の勾配
    grad['b2'] = np.sum(delta2, axis=0)
    # W2の勾配
    grad['W2'] = np.dot(z1.T, delta2)
    # 中間層でのデルタ  
    #delta1 = np.dot(delta2, W2.T) * functions.d_relu(z1)

    ## 試してみよう
    delta1 = np.dot(delta2, W2.T) * functions.d_sigmoid(z1)

    delta1 = delta1[np.newaxis, :]
    # b1の勾配
    grad['b1'] = np.sum(delta1, axis=0)
    x = x[np.newaxis, :]
    # W1の勾配
    grad['W1'] = np.dot(x.T, delta1)
    
    # print_vec("偏微分_重み1", grad["W1"])
    # print_vec("偏微分_重み2", grad["W2"])
    # print_vec("偏微分_バイアス1", grad["b1"])
    # print_vec("偏微分_バイアス2", grad["b2"])

    return grad
```
