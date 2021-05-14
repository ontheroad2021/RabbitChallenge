# 深層学習 day１ Section５：誤差逆伝播法

## 確認テスト１

誤差逆伝播法では不要な再帰的処理を避ける事が出来る。既に行った計算結果を保持しているソースコードを抽出せよ。

解答：

```
# 出力層でのデルタ
delta2 = functions.d_mean_squared_error(d, y)
```

以下に見られるようにdelta2は多くの箇所で使用されている。

```
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
```  
  

## 確認テスト２

空欄に該当するソースコードを探せ。

解答：




