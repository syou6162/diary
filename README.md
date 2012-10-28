
# 2012-10-28

## What's Wrong???
係り受け解析とかアライメントとかある程度高次のNLPのタスクを扱っているとエラー分析が割と大変になってくる(CoNLLのフォーマットだけ見てエラー分析はつらい...)。どう改善すればよいかの糸口を得るためにもエラー分析は重要。それをビジュアルにできるツールがあるので紹介。

- [whatswrong - What's Wrong With My NLP? - Google Project Hosting](https://code.google.com/p/whatswrong/)

同時解析とかJoint Inferenceとかの研究で有名な[Sebastian Riedel](http://riedelcastro.github.com/)さんが作ったツール。

- syntactic dependency graphs
- semantic dependency graphs (a la CoNLL 2008)
- Chunks (such as syntactic chunks, NER chunks, SRL chunks etc.)
- Bilingual alignments
- BioNLP events, proteins, locations

などなど、shared-taskをベースにしてやる人にはありがたいツールである。ちなみに、こんな感じの出力が出る。

![bionlp09](http://cdn-ak.f.st-hatena.com/images/fotolife/s/syou6162/20121029/20121029012202.png)
![CoNLL2003](http://cdn-ak.f.st-hatena.com/images/fotolife/s/syou6162/20121029/20121029012203.png)

黒はgoldのデータと予測したものが一致した箇所、青は(予測のほうは外れてて)goldが出したところ、赤は予測のほうが外して出しちゃったやつ、となる。ちなみにdependency parsingの出力をclojureから出すだけならこんな感じで割と簡単にやることができる。

- [syou6162/dorothy-example · GitHub](https://github.com/syou6162/dorothy-example)

# 2012-10-26

## 読了

- [Amazon.co.jp： 図書館革命 図書館戦争シリーズ４ (角川文庫): 有川 浩, 徒花 スクモ: 本](http://www.amazon.co.jp/dp/4043898088/)

はー、ベタベタでよかった。別冊も引き続き読みたい。

# 2012-10-18

## 読了

- [Amazon.co.jp： 図書館危機 図書館戦争シリーズ３ (角川文庫): 有川 浩,徒花 スクモ: 本](http://www.amazon.co.jp/dp/404389807X/)

よいのだけれども、朝からにやけてしまうので通勤の読書に向いているか分からなくなってきたw。

# 2012-10-13

## まどマギ映画
気晴らしに遊びにでも行かんとやってられん、ってことでまどマギの友達と一緒に前後編を一日で見てきました。

- [劇場版 魔法少女まどか☆マギカ](http://www.madoka-magica.com/)

今日から後編が見れるようになったってことで結構混んでいた。。。さやかに妙に感情移入してしまっていた。

# 2012-10-12

## ex-ic
研修の移動で新幹線をよく利用することになりそうなのでex-icを使うようになったのだが、直前でも予約できてなかなか便利。ただ、スマホだと若干使い勝手が悪いなぁ。。。

あと、icocaをsmart icocaに進化させた。

## 読了
笠原いいね。展開的に続きが気になってきた。

- [Amazon.co.jp： 図書館内乱 図書館戦争シリーズ（２） (角川文庫): 有川 浩,徒花 スクモ: 本](http://www.amazon.co.jp/dp/4043898061/)

3巻以降を買った&貸してもらった。

# 2012-10-07

## Clojureで多クラス分類器
[今年の春の開発合宿](https://gist.github.com/57249e4e38ecf6aa37b6)でFOBOSを使ってお手軽単語分割器を書いた(デモは[ここ](http://yasuhisay.info/tiny_word_segmenter)に置いてる)のだけど、そのときには2値分類器を作っていた。そういえば多クラス分類器は作ってなかったなーと思ったので、[これ](https://github.com/syou6162/fobos_clj)をベースにして作った。

- [syou6162/fobos_multiclass_clj](https://github.com/syou6162/fobos_multiclass_clj)

といっても1 vs restでやるだけの簡単なやつです。でも、clojureだけで動くと何かと便利なので。libsvm形式とかに一回用意しないといけないとかは面倒だけど、このライブラリだと

```clj
(def training-example
  [["A" ["hoge" 1] ["fuga" 1]]
   ["B" ["piyo" 1] ["nyan" 1]]
   ["A" ["hoge" 1]]])
```

みたいな形でデータとラベルをつっこめるような感じにした。

# 2012-10-06

## 24を見た
- [24 -TWENTY FOUR- - Hulu](http://www.hulu.jp/24)

毎回気の抜けないストーリー展開だったので、見終わって非常に疲れた。。。色んな正義が交錯。

# 2012-10-05

## Clojureでtemp fileを操作する
`with-open`っぽくやりたいですよね、ってことで。

- [pallet/src/pallet/utils.clj at 7c301919ba585c9a8bfb92d9518f8f7431a1001e · tbatchelli/pallet](https://github.com/tbatchelli/pallet/blob/7c301919ba585c9a8bfb92d9518f8f7431a1001e/src/pallet/utils.clj#L128)

```clj
(require [clojure.java.io :as io])

(defmacro with-temp-file
  [[varname & [content]] & body]
  `(let [~varname (java.io.File/createTempFile "stevedore", ".tmp")]
     (when-let [content# ~content]
       (io/copy content# ~varname))
     (let [rv# (do ~@body)]
       (.delete ~varname)
       rv#)))

;; 使い方
(with-temp-file [file-obj (str (repeat 100000 "content"))]
  (.length file-obj))
```

## leinでlocalのjarを参照する
clojarsとかに入っていなかった場合などなど。ここではJavaのハイパフォーマンスなコレクションのライブラリである[Trove](http://trove.starlight-systems.com/)のjarをleinで追加したい場合を考える。以下のリポジトリを使う。

- [kumarshantanu/lein-localrepo](https://github.com/kumarshantanu/lein-localrepo)

`project.clj`にこんな感じで記述する。

```clj
(defproject seq-dep "0.1.0-SNAPSHOT"
  :description "FIXME: write description"
  :url "http://example.com/FIXME"
  :license {:name "Eclipse Public License"
            :url "http://www.eclipse.org/legal/epl-v10.html"}
  :dependencies [[org.clojure/clojure "1.4.0"]
                 [fobos_clj "0.0.2"]
                 [gnu/trove "1.0"]]
  :plugins [[lein-swank "1.4.4"]
            [lein-localrepo "0.4.1"]]
  :java-source-paths ["src/java/"]
  :main seq-dep.core)
```

これでいい感じにjarを配置してくれる。

```sh
% lein localrepo install src/java/lib/trove.jar gnu/trove 1.0
```

# 2012-10-03

## 読了
- [Amazon.co.jp： 図書館戦争 図書館戦争シリーズ（１） (角川文庫): 有川 浩,徒花 スクモ: 本](http://www.amazon.co.jp/dp/4043898053/)

# 2012-10-01
- 今年度も下期に突入
- 10月はやたらと研修があって、何回も東京に行かないといけない
 - 京阪奈はこういうときに少しあれだ

# 2012-09-30

## hulu
台風がきていて外に出れねーと思っていて気がついたらアカウントを作っていた。

- [Hulu - 人気映画やテレビ番組がお手軽に見放題](http://www.hulu.jp/)

# 2012-09-28

## 生のJavaファイルをClojureから使う
例えば[この辺](https://github.com/aria42/umass-nlp)をclojureから触りたいなーって思ったとしよう。こいつはjarで固められていないので、自分でどうにかしないといけない。そのやり方とかがちょっと分からなくなったのでメモしておく。

まず、project.cljを用意する。`java-source-paths`とかをきちんと書いてやる。

```clj
(defproject hoge "0.1.0-SNAPSHOT"
  :description "FIXME: write description"
  :url "http://example.com/FIXME"
  :license {:name "Eclipse Public License"
            :url "http://www.eclipse.org/legal/epl-v10.html"}
  :dependencies [[org.clojure/clojure "1.4.0"]
                 [log4j/log4j "1.2.16"]
                 [commons-primitives/commons-primitives "1.0"]
                 [org.yaml/snakeyaml "1.5"]
                 [net.htmlparser.jericho/jericho-html "3.1"]]
  :java-source-paths ["edu/"])
```

(cljファイルではなく)javaファイルをコンパイルする。若干警告が出てるけど、気にしない。

```
% lein javac
Compiling 95 source files to /Users/yasuhisa/Desktop/umass-nlp/src/main/java/hoge/target/classes
注:入力ファイルの操作のうち、未チェックまたは安全ではないものがあります。
注:詳細については、-Xlint:unchecked オプションを指定して再コンパイルしてください。
```

このディレクトリで

```
% pwd
/Users/yasuhisa/Desktop/umass-nlp/src/main/java/hoge/target/classes
```

こういう感じのクラスパスを付けてあげれば動く。これでとりあえずjarが提供されていないようなものについても触れるようになったのでちょっと安心である。

```sh
% java -classpath /Users/yasuhisa/.m2/repository/log4j/log4j/1.2.16/log4j-1.2.16.jar:/Users/yasuhisa/.m2/repository/commons-primitives/commons-primitives/1.0/commons-primitives-1.0.jar:. edu.umass.nlp.examples.HMMTest
```

# 2012-09-26

## git rebase関係

つぎはぎになっていた付近をきちんとgitに追加していく簡単ではないお仕事。「あー、あのコミットに追加しそこねた!!」ってやつがあったときに初めてgit rebaseを使った。ここが分かりやすかった。

- [古いコミットを書き換える： 歴史修正主義者のための git rebase -i 入門 - 学習する機械、学習しない人間](http://d.hatena.ne.jp/okmount/20091021/p1#20091021f1)

基本的には書き換えたいコミットの一つ前に戻って`git commit --amend`、終わったら`git rebase --continue`していけばよい。ミスったら`git rebase --abort`で戻れます。

---

rebaseするときにとりあえずstashで退避しておいて、戻したらconflictってことがときどきある。そのときはファイルを選択してcheckout、みたいなことができる。

```sh
git stash list
```

で今あるスタッシュのリストを見て、具体的なファイルの変更点が知りたかったら

```sh
git show stash@{0}:test/PivotGenerativeModel/test/util.clj
```

で見ればよく、戻したかったらこんな感じで戻せる。

```sh
git checkout stash@{0} test/PivotGenerativeModel/test/util.clj
```

- [git-stashしたファイルをapplyしようとしてコンフリクトしたときの解決法 - 豆無日記](http://d.hatena.ne.jp/nobeans/20090525/1243269992)

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
