# 深層学習 day１ Section３：出力層

## 確認テスト１

誤差関数（２乗和誤差、残差平方和）において、
* なぜ、引き算するのみではなく、二乗するのか述べよ
* 1/2はどういう意味を持つか述べよ

解答：

* 全体でどれ位誤差があったかを知りたいとき、引き算したものの総和はゼロになる。
  各々を二乗したものを足し合わせる事によって、それを防ぐ事ができる。
* 誤差逆伝播の計算で、誤差関数を微分する必要があるのだが、その際に1/2があると係数が相殺される計算式が簡単になるため。
   

## 確認テスト２

以下の数式に該当するソースコードを示し、一行づつ処理の説明をせよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}f(i,u)={\dfrac{e^{u_i}}{\sum_{k=1}^{n}e^{u_k}}}\end{align*}">  
</p>

解答：

処理として本質的なのは下になる。
```
np.exp(x) / np.sum(np.exp(x))
``` 

下のソフトマックス関数内において、If文の中はミニバッチとしてデータが取り扱われる時に使用される。その時に入力として入ってくるｘの行列の形が少し違うので以下の様な処理に変わっている。

```    
# 出力層の活性化関数
# ソフトマックス関数
def softmax(x):
    if x.ndim == 2:
        x = x.T
        x = x - np.max(x, axis=0)
        y = np.exp(x) / np.sum(np.exp(x), axis=0)
        return y.T

    x = x - np.max(x) # オーバーフロー対策
    return np.exp(x) / np.sum(np.exp(x))
```

## 確認テスト３

以下の数式に該当するソースコードを示し、一行づつ処理の説明をせよ。

<p align="center">
    <img src="https://latex.codecogs.com/svg.latex?\begin{align*}E_n(\mathbf{w})={-\sum_{i=1}^{l}d_i\log%20y_i}\end{align*}">  
</p>

解答：

処理として本質的なのは下になる。
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
