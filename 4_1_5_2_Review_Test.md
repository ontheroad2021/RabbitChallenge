# 深層学習 day３ Section５：Ｓｅｑ２ｓｅｑ

## 確認テスト１

下記の選択肢から、ｓｅｑ２ｓｅｑについて説明しているものを選べ。  
（１）時刻に関して順方向と逆方向のＲＮＮを構成し、それら２つの中間層表現を特徴量として利用するものである。  
（２）ＲＮＮを用いたＥｎｃｏｄｅｒ－Ｄｅｃｏｄｅｒモデルの一種であり、機械翻訳などのモデルに使われる。  
（３）構文木などの木構造に対して、隣接単語から表現ベクトル（フレーズ）を作るという演算を再帰的に行い（重みは共通）、文全体の表現ベクトルを得るニューラルネットワークである。  
（４）ＲＮＮの一種であり、単純なＲＮＮにおいて問題となる勾配消失問題をＣＥＣとゲートの概念を導入することで解決したものである。  


解答：（２）

（１）双方向ＲＮＮ  
（２）構文木  
（３）ＬＳＴＭ  
   

## 確認テスト２

Ｓｅｑ２ｓｅｑとＨＲＥＤ、ＨＲＥＤとＶＨＲＥＤの違いを簡潔に述べよ。


解答：

- Ｓｅｑ２ｓｅｑは１問１答しかできない（問に対して文脈も何もなく、ただ応答が行われ続ける）。  
ＨＲＥＤは文章の過去の文脈というものを考慮できる。  

- ＨＲＥＤは確かに文脈を意識した文を作る事ができるのだが、ありがちな答えしか出さなくなる。例）「うん」「そうだね」等。  
ＶＨＲＥＤは文脈を意識しながら文を生成するモデルにヴァリエーションを持たせられるように工夫をしてみようという仕組みである。


## 確認テスト３

ＶＡＥに関する下記の説明文中の空欄に当てはまる言葉を答えよ。自己符号化器の潜在変数に____を導入したもの。   

解答：

確率分布