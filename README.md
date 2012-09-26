# 2012-09-26

## 読了

- [Amazon.co.jp： 太陽の塔 (新潮文庫): 森見 登美彦: 本](http://www.amazon.co.jp/dp/4101290512/)

# 2012-09-25

## Linuxで同じファイルを書き換える
例えば`file.txt`っていうファイルがあったときに、行毎にシャッフルしてから同じ`file.txt`にまたそれを書きたい。`nkf --overwrite`みたいなことがしたい。リダイレクトだとそういうことできないのかと思って中間ファイルを作っていたけど、ちゃんとありました。

```sh
% echo hoge fuga piyo > test.txt
% cat test.txt
hoge fuga piyo
% echo xxxxx >! test.txt
% cat test.txt
xxxxx
```

## Gitで日本語ファイル名を扱う
普段ならそんなことしないんだが、会社的な都合でファイルの命名規則が決まっていたりする場合があって、そういうとき用に。以下で設定ができる。

```sh
git config --global core.quotepath false
```

# 2012-09-24

## HandBrakeのCUIで字幕を埋め込む
以前はGUIでポチポチ押していってたんですが、やる量が多くなると面倒なことこの上ないので自動化自動化。

- [DVDをmpegにしておく - Seeking for my unique color.](http://d.hatena.ne.jp/syou6162/20120111/1326210413)

こんなスクリプトを適当に書きました。字幕を埋め込みにしないとiPhoneじゃ見れないのでちょっと苦労した。

- [HandBrakeのCLIでmp4に変換 — Gist](https://gist.github.com/3776204)

## 読了
読み終わった。面白かったので、続きも買おっと。

- [Amazon.co.jp： 武士道シックスティーン (文春文庫): 誉田 哲也: 本](http://www.amazon.co.jp/dp/4167780011/)

最近、朝の通勤時間は読書時間に割り当てられております。

# 2012-09-22

## 関東に遊びに行きました
これまた一ヶ月くらい前の(ry、ですが。夏期休暇を使って東京に行きました。主に人と会っていたのですが、人の写真は勝手に上げれないので必然的に食べものの写真ばかりに。横須賀の刺身がおいしかったです。パンは渋谷の駅に最近できたパン屋さん。

![きゅうり](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0411.jpg)
![サラダ](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0412.jpg)
![ハモ](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0414.jpg)
![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0415.jpg)
![刺身](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0417.jpg)

![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0425.jpg)
![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0426.jpg)
![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0427.jpg)
![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0428.jpg)

最後はビール飲んでた。

![](https://raw.github.com/gist/e18ddb934109a52e34f9/shrinked-IMGP0458.jpg)

## 京都、自転車旅
もう一ヶ月前くらいですけど、カメラの練習がてら(最近そればっかりですw)京都市内を自転車で周りました。この本を参考にしてルートを決めました。

- [Amazon.co.jp： 京都自転車デイズ: ワークルーム: 本](http://www.amazon.co.jp/dp/4838104103/)

### 出発

![当日乗って行った自転車](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0296.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0287.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0281.jpg)

### 八坂の塔

![八坂の塔](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0298.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0306.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0315.jpg)

### 円塔公園

![円塔公園](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0328.jpg)

### 八坂神社

![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0345.jpg)
![京都っぽい雰囲気の人力車](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0347.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0352.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0362.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0368.jpg)
![](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0373.jpg)

### 御所

![御所](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0387.jpg)

### ご飯系

![昼御飯](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0405.jpg)
![白玉](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0408.jpg)

### 夜景

![月](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0643.jpg)
![京都タワー](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0618.jpg)
![夜景](https://raw.github.com/gist/e5bd13178d9eb586d8fb/shrinked-IMGP0667.jpg)

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
