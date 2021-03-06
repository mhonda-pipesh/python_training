# Program

## 目的

* 基礎的なPython開発能力の習得
* Pythonを利用しWebアクセスを行う手法の取得

## 注意点

Python Basic、Extraの1までは最低限達成するライン。それ以降はどこまででもOK。

* 研修で開発したコードは[GitHub](https://github.com/)に上げてください(個人のPublicでOK)。この記事のコメントに各自リポジトリへのリンクを張ってください。※不要なファイルは.gitignoreで除外すること。詳細はセットアップの記事参照
* README.mdに、自分のプログラムのセットアップ方法、実行確認方法をきちんと書くこと。

実習について

* Pythonは3です
* 課題ごとにファイルを作成するか、複数の課題をまとめるかは任意です。ただ、上記にあるとおり実行結果を確認する方法をREADMEにきちんと記載してください。
* 「出力せよ」という場合は、ファイルで出力を行ってください(ファイル名は適当で構いません)
* 「表示せよ」という場合は、コンソール表示のみで構いません。ただ、出力が膨大になる場合はトップNに限定するなど、工夫すること

コードはPython3ライクに書くこと(withとか)。デザインパターンの研修も並行しますが、設計のきれいさ・可読性を意識してコーディングしてください([参考](http://qiita.com/icoxfog417/items/f737d6c84b733f649461))。

# Assignments

## Python Basic

以下の演習にはこのファイルを使用してください。

[address.txt](https://drive.google.com/file/d/0B1mQfOwV0VUHVG1aeGtJTVZWQVE/view?usp=sharing)

1. ファイルの行数をカウントせよ
2. タブ１文字につきスペース１文字に置換せよ
3. 各行の１列目だけを抜き出したものをcol1.txtに、２列目だけを抜き出したものをcol2.txtとしてファイルに保存せよ
4. 3で作ったcol1.txtとcol2.txtを結合し，元のタブ区切りテキストを復元せよ
5. 自然数Nをコマンドライン引数にとり、入力のうち先頭のN行だけ出力せよ
6. 自然数Nをコマンドライン引数にとり、入力のうち末尾のN行だけ出力せよ
7. １コラム目の文字列を集計して表示せよ(文字列/カウントを表示）
8. 各行を２コラム目の辞書順にソートして出力せよ
9. 各行を２コラム目、１コラム目の優先順位で辞書の逆順にソートして出力せよ
10. 各行の２コラム目の文字列の出現頻度を求め、出現頻度の高い順に並べよ。ただし、3で作成したプログラムの出力（col2.txt）を読み込むプログラムとして実装せよ


## Python Extra

以下の演習ではぐるなびのAPIを利用して下さい。1以外は難易度高めなので、できないからといって焦る必要はありません。

[ぐるなび for Developers](http://api.gnavi.co.jp/api/manual/restsearch/)

1. コマンドライン引数から検索キーワードを受け取り、ぐるなびAPIにアクセスし検索結果(店舗名)を出力せよ。受け取るデータ型はJSON形式にすること
2. コマンドライン引数から受け取った検索キーワードが日本語かどうか判定し、それにより利用する検索APIをそれぞれレストラン検索API/多言語版レストラン検索APIで切り替えよ。なお、条件により対応するAPIの数は今後増えていくということを考慮した設計にすること
3. コマンドラインから[都道府県番号](http://ja.wikipedia.org/wiki/%E5%85%A8%E5%9B%BD%E5%9C%B0%E6%96%B9%E5%85%AC%E5%85%B1%E5%9B%A3%E4%BD%93%E3%82%B3%E3%83%BC%E3%83%89)も受け取れるようにせよ(番号の頭0は不要。また、都道府県を指定するかは任意とする)
4. 応援APIを利用し、各店舗の応援を取得せよ。取得するのは上位3件の店舗分のみで構わないが、この指定が今後変えられるよう考慮すること。なお、取得処理は並列で実行すること（asyncioを使用）。
5. 店舗名・リンク・画像・応援の最低4点を含むhtmlページ(上位3件のみで可)を作成し、ブラウザでページを開け([参考](http://programminghistorian.org/lessons/creating-and-viewing-html-files-with-python) ただしPython2で書かれているようなので注意)

## Python Free Assignment

お題

「昼休みを有効に使うためのコンソールアプリケーション」

昼休み中バッチ実行するもよし、昼休みに向けて何かデータを取るもよし、昼休みを有効に使うためのアプリケーションを作ってみてください。

WebAPIなどはこちらを参考にしてください

[MA](http://mashupaward.jp/apis)


# Example Answer

## Python Basic

* 実装: `basic/python_basic.py`
* テスト: `basic/tests/test_python_basic.py`

テストの実行

```
python -m unittest basic/tests/test_python_basic.py
```

コマンドライン引数を取る課題(5・6)については、コンソールから以下のように実行して動作を確認できます(-hで利用方法の説明を表示可能です)。

```
# 上位5件を表示
python basic/python_basic.py ./data/address.txt 5 --part h

# 下位5件を表示
python basic/python_basic.py ./data/address.txt 5 --part t
```

## Python Extra

ぐるなびAPIのキーが必要になります。以下の開発者用サイトから登録してAPIキーを取得してください。  

[ぐるなびWebサービス for Developer](http://api.gnavi.co.jp/api/)

`gurunabi_service.py`と同じフォルダに以下フォーマットで`api_key.json`を作成し、取得したAPIキーを設定してください。

```
{
  "keyid": "xxxx"
}
```

* 実装: `basic/python_extra.py`
* テスト: `extra/tests/test_python_extra.py`

テストの実行

```
python -m unittest extra/tests/test_python_extra.py
```

コマンドラインツールとしての利用(-hで利用方法の説明を表示可能です)

```
python extra/python_extra.py 和食
```
