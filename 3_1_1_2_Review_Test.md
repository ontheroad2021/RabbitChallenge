# 深層学習 day１ Section１：入力層～中間層

## 確認テスト１

与えられた図式に動物分類の実例を入れてみよう。

解答：

   ![GitHub Logo](/images/3_1_1_2_Review_Test_01.png)

## 確認テスト２

以下の数式をPythonで書け。

<p align="center">
  <img src="https://latex.codecogs.com/svg.latex?\begin{align*}u&=w_1x_1+w_2x_2+w_3x_3+w_4x_4+b\\&=\mathbf{W}\mathbf{x}+b\end{align*}" />
</P>

解答：
```
u = np.dot(x, W) + b
```

## 確認テスト３

1-1のファイルから中間層を定義しているソースを抜き出せ。

解答：
```
# 2層の総入力
u2 = np.dot(z1, W2) + b2
    
# 2層の総出力
z2 = functions.relu(u2)
```    
