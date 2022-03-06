# 1. Hello World!

はじめてプログラムを学ぶ人は大抵、まず最初に `Hello World!` と表示するプログラムを書きます。ここでもそれに乗っ取って、スプレッドシートに `Hello World!` と表示するプログラムを書いてみましょう。

## 1.1. はじめての Hello World

新規に Google スプレッドシートを作成し、メニューの `拡張機能 → Apps Script` を選択します。
すると、Apps Script というタブが新しく開きます。ここで先ほど作成したスプレッドシートで動かすプログラムを編集することができます。この中に、`コード.gs` というファイルが作成されていると思います。
`コード.gs` のファイルの中身は次のようになっているはずです:

``` javascript
function myFunction() {
}
```

この `コード.gs` の内容を以下のように書き換えてください:

``` javascript
function myFunction() {
  console.log("Hello, World!");
}
```

書き換えが終わったら、あなたが書いたソースコードの少し上にフロッピーディスクのマーク (:floppy_disk:) があるので、それをクリックして保存します。

今クリックした保存ボタンの右に "実行" と書かれたボタンがあるので、クリックしてみましょう。ソースコードの下の方に "実行ログ" なるものが表示され、以下のようなものが出てくるはずです:

```
21:28:30	お知らせ	実行開始
21:28:30	情報	Hello, World!
21:28:31	お知らせ	実行完了
```

おめでとうございます！あなたが書いたプログラムが実行され、`Hello, World!` と表示されました！

## 1.2. 実行ログ

あなたが先ほど `Hello, World!` と表示させたのは "実行ログ" と呼ばれるものです。実行ログには、プログラムを実行した際に補助的な情報等が表示されます。補助的な情報とは例えば "〇〇を実行しました" や "〇〇にエラーがあります" 等といったメッセージです。そういったメッセージを総称して "ログ" と呼びます。プログラムを書いていてうまく動かなかった時などに、この実行ログに解決のための情報がないか確認するのです。

Google Apps Script では、ブラウザ上から実行ログを確認できる機能を提供していますが、世の中のプログラマはそれを "コンソール" と呼ばれるものから確認します。プログラマは黒い画面に何やら難しそうな文字を打っているイメージがあると思いますが、その黒い画面がコンソールです。"コマンドプロンプト" や "ターミナル" と呼ばれたりもしますが、大体同じものです。

先ほど `コード.gs` の中に以下のような文字列を書きました:

``` javascript
  console.log("Hello, World!");
```

これはコンソールに `Hello, World!` という文字列を出してね、という命令です。`console` さんに `log` を出力してね、出力する内容は `"Hello, World!"` だよ、と命令していると思ってもらえればいいでしょう。

## 1.3. スプレッドシートに Hello World を表示する

しかし、我々はコンソールに文字列を表示するプログラムを書きたいわけではありません。スプレッドシートに色々な計算をした結果を出したいのです。
なので今度は、スプレッドシートに `Hello, World` と表示してみましょう。

先ほどの `コード.gs` を以下のように書き換えます:

``` javascript
function myFunction() {
  console.log("Hello, World!");

  // ここから追加
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getActiveSheet();
  sheet.getRange("A1").setValue("Hello, World!");
}
```

書き換えたら、先ほどと同様保存した後、実行ボタンを押してみましょう。その際権限の確認等が出てくるかもしれないですが、許可してください。

このプログラムを実行すると、実行ログには先ほどと同様

```
21:28:30	お知らせ	実行開始
21:28:30	情報	Hello, World!
21:28:31	お知らせ	実行完了
```

と表示されます。では、最初に作ったスプレッドシートを見てみましょう。
A1 のセルに `Hello, World!` と表示されているはずです。
これであなたもスプレッドシートを操作するプログラムを書くことができました、おめでとうございます！

先ほど追加したコードの解説は次の章で行いますが、最後の

``` javascript
  sheet.getRange("A1").setValue("Hello, World!");
```

を見れば、なんとなくこのプログラムを実行することで何が起こったのか分かると思います。

## 1.4. 演習問題

`コード.gs` を書き換えて、以下のようなことをするプログラムを書いてみましょう:

1. 実行ログにあなたの名前を表示するプログラムを書いてください。
2. スプレッドシートの B1 セルにあなたの名前を表示するプログラムを書いてください。