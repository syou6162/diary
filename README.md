
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

# 2012-09-16

## compojureでrestartかけずにファイルの反映をさせる
起動になかなか時間がかかるので。。。`[ring-reload-modified "0.1.1"]`をproject.cljに記述して。`[ring.middleware.reload-modified]`をuseした後に

```clj
(def app (wrap-reload-modified #'routes ["src"]))
```

などとやればおk。
