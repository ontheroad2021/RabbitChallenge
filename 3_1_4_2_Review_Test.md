# 深層学習 day１ Section４：勾配降下法

## 確認テスト１

以下の勾配降下法に該当するソースコードを探してみよう。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}\mathbf{w}^{(t+1)}&=\mathbf{w}^{(t)}-\varepsilon\nabla%20E\end{align*}"> 
</P>

解答：

* 全体でどれ位誤差があったかを知りたいとき、引き算したものの総和はゼロになる。
  各々を二乗したものを足し合わせる事によって、それを防ぐ事ができる。
* 誤差逆伝播の計算で、誤差関数を微分する必要があるのだが、その際に1/2があると係数が相殺される計算式が簡単になるため。
   

## 確認テスト２

オンライン学習とは。

解答：

学習データが入ってくる度に都度パラメータ（重み）を更新し、学習を進めていく方法。一方、バッチ学習では一度にすべての学習データを使用してパラメータ更新を行う。最近の深層学習ではオンライン学習というのがかなり重要な要素になっています。


## 確認テスト３

以下の数式に該当するソースコードを示し、一行づつ処理の説明をせよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}E_n(\mathbf{w})={-\sum_{i=1}^{l}d_i\log%20y_i}\end{align*}">  
</p>

解答：

処理として本質的なのは下になる。

* 対数関数の性質上、０に近づくと－∞に落ちてしまう。それを避けるために小さな値（1e-7）を付与している。
* yには０と１が並んでいる（正解に１が立っている）。
* dとはニューラルネットがd番目が正解であろうと思った場所。

```
-np.sum(np.log(y[np.arange(batch_size), d] + 1e-7))
``` 

```    
# クロスエントロピー
def cross_entropy_error(d, y):
    if y.ndim == 1:
        d = d.reshape(1, d.size)
        y = y.reshape(1, y.size)
        
    # 教師データがone-hot-vectorの場合、正解ラベルのインデックスに変換
    if d.size == y.size:
        d = d.argmax(axis=1)
             
    batch_size = y.shape[0]
    return -np.sum(np.log(y[np.arange(batch_size), d] + 1e-7)) / batch_size
```
