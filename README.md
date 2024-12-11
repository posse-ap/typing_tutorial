# アプリ開発体験 〜タイピングゲームを作ろう〜

このワークショップでは、HTML、CSS、JavaScriptを使い、タイピングゲームをテーマとしたWebアプリの開発を体験できます！

まずはインプットから始め、HTML、CSS、JavaScriptの基本を学び、その後、実際にタイピングゲームを作りながら、Webアプリの仕組みを理解していきます。

## ■Webアプリとは

Webアプリとは、インターネットを通じて利用できるアプリケーションのことです。

ブラウザを使って動作するため、特別なインストールは必要ありません。

Webアプリにはどのようなものがあるでしょうか？普段使っているWebアプリを考えてみましょう。

## ■HTMLとは

HTMLは、Webページの「骨組み」を作るための言語です。

例えば、文字やボタン、画像など、画面に表示する要素を定義します。

### ◯文字を表示する

HTMLでは`<p>`タグを使って、文章やメッセージを表示します。

以下のコードを`body`タグ内に追加すると、画面に「こんにちは！」と表示されます。

```html
<p>こんにちは！</p>
```

### ◯見出しを表示する

見出しを表示するには、`<h1>`から`<h6>`までのタグを使います。

```html
<h1>見出し1</h1>
<h2>見出し2</h2>
<h3>見出し3</h3>
```

### ◯テキストボックス

タイピングゲームでは、ユーザーが文字を入力するためのテキストボックスが必要です。

HTMLでは`<input>`タグを使います。

```html
<input type="text" />
```

### ◯ボタン

ゲームのリセットボタンなど、クリックして動作を実行するためのボタンを作れます。

```html
<button>リセット</button>
```

### ◯画像

ゲームにアイコンや装飾を追加するときには、 `<img>`タグを使います。

```html
<img src="path/to/image.jpg" alt="画像の説明" />
```

---

### ◯チェックポイント: 自己紹介ページを作ろう

上で学んだ内容をもとに、自己紹介ページを作ってみましょう！

例えば以下のような内容を表示するページを作ってみてください。

1. 自己紹介のタイトルを表示する
2. 名前、趣味、好きな食べ物などの情報を表示する
3. 好きな画像を表示する

```html
<h1>自己紹介</h1>
<p>名前: 〇〇</p>
<p>趣味: △△</p>
<p>好きな食べ物: □□</p>
<img src="path/to/image.jpg" alt="自分の写真" />
```

---

## ■CSSとは

CSSはWebページのデザインやレイアウトを整えるための言語です。

今回はTailwind CSSというCSSフレームワークを使います。

Tailwind CSSを使うと、あらかじめ用意されたクラス名をHTMLに追加するだけでデザインが適用されるので、とても便利です。

### ◯Tailwind CSSを使う準備
Tailwind CSSを利用するには、HTMLファイルの`<head>`部分に以下のスクリプトを追加します。

```html
<script src="https://cdn.tailwindcss.com"></script>
```

Tailwind CSSを読み込むと、見出しなどのデフォルトのスタイルがなくなります。

### ◯色をつける

Tailwind CSSを使えば、テキストや背景、ボーダーに簡単に色をつけられます。

#### テキストの色
```html
<p class="text-red-500">この文字は赤色です。</p>
<p class="text-blue-700">この文字は青色です。</p>
```

#### 背景の色
```html
<div class="bg-green-200">背景が緑色です。</div>
<div class="bg-gray-900 text-white">ダークモード風の背景です。</div>
```

#### 枠線の色
```html
<div class="border-2 border-yellow-500">黄色の枠線があります。</div>
```

### ◯大きさを変える

文字のサイズやボックスの大きさもTailwind CSSで簡単に指定できます。

#### 文字サイズ
```html
<p class="text-xl">少し大きな文字です。</p>
<p class="text-4xl">かなり大きな文字です。</p>
```

#### 文字の太さ
```html
<p class="font-bold">太字の文字です。</p>
```

#### ボックスのサイズ
```html
<div class="w-64 h-32 bg-blue-100">幅が64、高さが32のボックス</div>
```

### ◯位置を変える

要素の配置を調整する方法を見ていきます。

#### テキストの揃え方
テキストの揃え方は、`text-left`、`text-center`、`text-right`を使って簡単に調整できます。
```html
<p class="text-left">左揃え</p>
<p class="text-center">中央揃え</p>
<p class="text-right">右揃え</p>
```

#### マージンとパディング
- マージン: 要素の外側の余白
- パディング: 要素の内側の余白

```html
<div class="m-4 p-8 bg-gray-300">
  外側に余白（マージン）が4、内側に余白（パディング）が8あります。
</div>
```

#### 横並びの配置

要素を横並びに配置するには、親要素に flex クラスを使います。これにより、デフォルトで子要素が横方向に並ぶようになります。

```html
<div class="flex justify-center items-center gap-4 bg-gray-100 p-8">
  <div class="bg-blue-500 w-16 h-16"></div>
  <div class="bg-red-500 w-8 h-8"></div>
  <div class="bg-green-500 w-4 h-4"></div>
</div>
```

- `flex`で子要素が横並びに
- `justify-center`で水平方向に中央寄せ
- `items-center`で水平方向に中央寄せ
- `gap-4`で子要素間の間隔を4に

### ◯影をつける

要素に影を追加して立体感を出せます。
```html
<div class="shadow-md p-4 bg-white">このボックスには影があります。</div>
```

### ◯その他便利な機能

#### 丸みをつける

角丸のボックスを作るには、`rounded`クラスを使います。
```html
<div class="rounded bg-blue-500 w-16 h-16"></div>
```

角丸の大きさを調整するには、`rounded-[サイズ]`クラスを使います。
```html
<div class="rounded-lg bg-blue-500 w-16 h-16"></div>
```

完全に丸いボックスを作るには、`rounded-full`クラスを使います。
```html
<div class="rounded-full bg-blue-500 w-16 h-16"></div>
```

#### 透明度を調整
```html
<div class="opacity-50 bg-red-500">半透明のボックス</div>
```

---

### ◯チェックポイント: デザインを整えよう

自己紹介ページにデザインを追加してみましょう！

例えば以下のようなデザインを追加してみてください。

1. ページ全体の背景色を変える
2. テキストの色を変える
3. ボックスの大きさを変える
4. テキストの配置を変える

```html
<div class="bg-gray-100 p-8">
  <h1 class="text-4xl text-center">自己紹介</h1>
  <p class="text-lg text-center">名前: 〇〇</p>
  <p class="text-lg text-center">趣味: △△</p>
  <p class="text-lg text-center">好きな食べ物: □□</p>
  <img src="path/to/image.jpg" alt="自分の写真" class="mx-auto mt-4 rounded-full" />
</div>
```

---

## ■JavaScriptとは
