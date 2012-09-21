
# 2012-09-21

## コマンドラインユーティリティツール群
調べものしてたら便利そうなの見つけた。

- [brendano/cmdutils](https://github.com/brendano/cmdutils)

Rとかを使っていたら、`mean`とか`sd`とか`summary`とかやりたくなってしまうから

```sh
# alias for stats functions
for f in mean sd max min
do
    alias $f="R --vanilla --slave -e \"x <- scan('stdin', quiet=TRUE); cat($f(x), fill=TRUE)\""
done
```

とかやっていたのだけれど、上のちっちゃいユーティリティツールみたいなののほうが使い勝手よさそう。

JSONで配列のある要素の統計量取りたい、みたいなときとか

```sh
% cat all.json | jsonrb 'puts self.map{|doc| doc.domain}' | summary
N = 26147 		17 unique values
Min   :  0
    25:  4
Median:  7 	Mean: 7.757 	SD: 4.901
    75:  11
Max   :  16
```

のようにできて便利。別に普通にスクリプトを書けばいいんだけど、ワンライナーでできるっていうのがいいところ。他にはこんなのが入ってた。

- approxwc => すんげーでかいファイルの行数とかおおまかに知る
- dateseq => 日付連番を作る
 - `dateseq 2012-09-21 2012-09-30`
- jsonpp => json整形してくれる
- mapagg => 入力の各行に対して何かやって、何かにまとめる。map reduceっぽい何か
- summary => Rの`summary`っぽい表示をしてくれる

# 2012-09-19

## 画像の縮小
markdownは画像のサイズを指定できないっぽいので、カメラで取った写真をそのまま貼るとアホみたいにでかくなる。というわけでその前に縮小したい。いっぱいあるのでコマンドラインで一括処理。

```sh
# convertコマンドはが入っていないなら以下で入れる
sudo port install ImageMagick +lcms +jpeg2
ls IMGP*.jpg | xargs -I@ convert -resize 20% @ shrinked-@
```

# 2012-09-18

## コマンドラインで簡単にお手軽markdownブラウザを作る
markdownのviewer(?)で何を使っているかと聞かれたので。

```sh
cd ~/bin
wget --no-check-certificate https://gist.github.com/raw/152480/41cf559e358fd4dc505af6679d382c3a5bcda3ad/kansit
sudo gem1.9 install kramdown
kansit -s "**/*.md" -c "kramdown < hoge.md  | nkf -w > test.html && open -g test.html"
```

これで自分の好きなエディタを使いながら、リアルタイムpreviewできるからそれでもうよくね?

# 2012-09-17

## 鞍馬と貴船に行ってきました
祝日ということだったので、友達と鞍馬と貴船に遊びに行ってきました。カメラの練習という意味を込めて写真多めでお送りします。

出発の出町柳駅。叡山電鉄には初めて乗りました。

![出町柳駅](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0711.jpg)

京阪奈も静かなところですが、いつもよりさらに静かでした。

![](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0717.jpg)
![](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0727.jpg)

![貴船駅](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0729.jpg)

下を川が流れている。雨天時は中止。

![](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0740.jpg)

![貴船神社入口1](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0743.jpg)
![貴船神社入口2](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0745.jpg)
![貴船神社1](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0746.jpg)
![貴船神社2](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0747.jpg)

水占い。何も書いてないけど...?

![水占いbefore](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0762.jpg)

水に付けると出てきました。大吉!

![大吉](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0764.jpg)

### 突然のそうめん!

人生初めての流しそうめんを体験しました。思ってたよりもどんどんくるので、写真取るの交代しながらじゃないと無理w。

![ひろ文](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0774.jpg)
![そうめん待ち](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0814.jpg)
![そうめんセット](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0827.jpg)
![そうめん1](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0833.jpg)
![そうめん2](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0834.jpg)
![そうめん3](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0835.jpg)
![そうめん4](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0836.jpg)
![そうめん5](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0837.jpg)

### 鞍馬寺

![天狗1](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0840.jpg)
![天狗2](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0841.jpg)

![お寺入口](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0844.jpg)
![](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0851.jpg)
![](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0859.jpg)
![ケーブルカー1](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0864.jpg)
![ケーブルカー2](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0868.jpg)

![のぼっている途中](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0873.jpg)
![本殿](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0878.jpg)
![上からの景色](https://raw.github.com/gist/f22a012421976b2daf5f/shrinked-IMGP0879.jpg)

# 2012-09-16

## compojureでrestartかけずにファイルの反映をさせる
起動になかなか時間がかかるので。。。`[ring-reload-modified "0.1.1"]`をproject.cljに記述して。`[ring.middleware.reload-modified]`をuseした後に

```clj
(def app (wrap-reload-modified #'routes ["src"]))
```

などとやればおk。
