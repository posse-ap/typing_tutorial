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

JavaScriptは、Webページに「動き」を加えるためのプログラミング言語です。
例えば、ボタンを押したらメッセージが表示される、文字が変わる、などの仕組みを作ることができます。

JavaScriptは、ブラウザの中で動いています。特別なアプリをインストールしなくても、みなさんのパソコンやスマートフォンにあるブラウザ（ChromeやSafariなど）で動作します。

今回は、簡単なプログラムを使って、JavaScriptがどのように動いているかを体験してみましょう！

### ◯JavaScriptの基本①

#### メッセージを表示する

まず`script.js`というファイルを開き、以下のコードを追加します。

```js
alert('Hello, World!');
```

すると、ページをリロードすると、`Hello, World!`というメッセージが表示されます。

また、`console.log`を使うと、ブラウザの`開発者ツール`の`コンソール`にメッセージを表示することができます。

以下のコードを追加した後、`F12`キーを押して開発者ツールを開き、`コンソール`タブを確認してみましょう。

```js
console.log('Hello, World!');
```

![](/images/2024-12-12-16-05-18.png)

#### 変数を使う

変数を使うことで、データを保存しておくことができます。

変数は、`let`を使って宣言します。

```js
// 文字列を保存する変数
let message = 'Hello, World!';
console.log(message);
```

```js
// 数値を保存する変数
let number = 123;
console.log(number);
```

また、変数は後から値を変更することができます。

```js
let message = 'Hello, World!';
console.log(message);

message = 'Goodbye, World!';
console.log(message);
```

#### ユーザーの入力を受け取る

`prompt`を使うと、ユーザーからの入力を受け取ることができます。

```js
let name = prompt('名前を入力してください');
console.log(name);
```

#### 演算

JavaScriptでは、四則演算をはじめ、様々な演算を行うことができます。

```js
let number = 123;
console.log(number);

// 数値を1増やす
// number = number + 1; と同じ
number += 1;
console.log(number);

// 数値を2倍にする
// number = number * 2; と同じ
number *= 2;
console.log(number);

// 数値を1減らす
// number = number - 1; と同じ
number -= 1;
console.log(number);

// 数値を半分にする
// number = number / 2; と同じ
number /= 2;
console.log(number);
```

文字列に`+`演算子を使うと、文字列を連結することができます。

```js
let message = 'Hello';
console.log(message);

message += ', World!';
console.log(message);
```

#### 複雑な文字列

バッククォート（`）を使うと、複数行の文字列を書くこともできます。

```js
let message = `こんにちは！
今日はいい天気ですね。
`;
console.log(message);
```

また、文字列の中に変数を埋め込むこともできます。

```js
let name = '山田';
let message = `こんにちは、${name}さん！`;
console.log(message);
```

この`${}`の中に変数を入れることで、変数の値を文字列に埋め込むことができます。

また、この中で演算を行うこともできます。

```js
let price = 100;
let quantity = 3;
let message = `単価: ${price}円
数量: ${quantity}個
合計: ${price * quantity}円
`;
console.log(message);
```

---

### ◯チェックポイント

ページを開いたら、ユーザーに名前を入力してもらい、入力された名前を表示するプログラムを作ってみましょう。

例えば以下のようになると良いです。
- 入力された名前: 山田
- 表示されるメッセージ: こんにちは、山田さん！

<details>
<summary>解答例</summary>

```js
let name = prompt('名前を入力してください');
let message = `こんにちは、${name}さん！`;
alert(message);
```

</details>

---

### ◯JavaScriptの基本②

#### 条件分岐

条件分岐を使うことで、特定の条件に応じて処理を変えることができます。

```js
let age = 20;

if (age >= 20) {
  console.log('成人です');
} else {
  console.log('未成年です');
}
```

条件の判定には、以下の演算子(比較演算子)を使います。

- `===`: 等しい
- `!==`: 等しくない
- `>`: より大きい
- `<`: より小さい
- `>=`: 以上
- `<=`: 以下

`age`の値を変えて、表示されるメッセージが変わることを確認してみましょう。

文字列の比較を行うこともできます。

```js
let password = 'password';

if (password === 'password') {
  console.log('パスワードが一致しました');
} else {
  console.log('パスワードが一致しません');
}
```

#### ループ処理

ループ処理を使うことで、同じ処理を繰り返すことができます。

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

`for`の中身は、以下のようになっています。

- `let i = 0`: 変数`i`を0で初期化
- `i < 5`: `i`が5未満の間、以下の処理を繰り返す
- `i++`: 処理が終わるたびに`i`を1増やす

#### 配列

配列を使うことで、複数のデータをまとめて扱うことができます。

```js
let fruits = ['りんご', 'バナナ', 'みかん'];
console.log(fruits[0]); // りんご
console.log(fruits[1]); // バナナ
console.log(fruits[2]); // みかん
```

配列の番号(インデックス)は、`0`から始まることに注意してください。

また、配列の要素数は、`length`プロパティで取得できます。

```js
let fruits = ['りんご', 'バナナ', 'みかん'];
console.log(fruits.length); // 3
```

これを使って、`for`ループを使って配列の要素を順番に表示することができます。

```js
let fruits = ['りんご', 'バナナ', 'みかん'];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

---

### ◯チェックポイント

ここでは、とてもシンプルなタイピングゲームを作ってみましょう。

ここに果物の一覧があります。
  
```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'melon'];
```

これらの果物を順番に表示し、ユーザーに入力してもらい、正解かどうかを判定するプログラムを作ってみましょう。

例えば以下のようになると良いです。

- 表示される果物: apple
- ユーザーの入力: apple
- 正解の場合: 正解！
- 不正解の場合: 不正解・・・
- これを5回繰り返す

これは少し難しいですが、頑張ってみてください！

<details>
<summary>解答例</summary>

```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'melon'];

for (let i = 0; i < fruits.length; i++) {
  let answer = prompt(fruits[i]);
  if (answer === fruits[i]) {
    alert('正解！');
  } else {
    alert('不正解・・・');
  }
}
```

</details>

もっと難しい問題に挑戦したい方は、正解数をカウントするプログラムに挑戦してみてください！

最後に

- 正解数
- 不正解数
- 正解率 (%)

を表示するようにしてみましょう。

<details>
<summary>解答例</summary>

```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'melon'];
let correct = 0;

for (let i = 0; i < fruits.length; i++) {
  let answer = prompt(fruits[i]);
  if (answer === fruits[i]) {
    alert('正解！');
    correct++;
  } else {
    alert('不正解・・・');
  }
}

let output = `正解数: ${correct}
不正解数: ${fruits.length - correct}
正解率: ${correct / fruits.length * 100}%`;
alert(output);
```

</details>

---

### ◯JavaScriptの基本③

ここからは、JavaScriptとHTMLを連携させて、Webページに動きをつける方法を学びます。

#### HTML要素を取得する

HTMLに以下の要素があるとします。

```html
<!-- index.html -->
<p id="example">こんにちは</p>
```

この要素をJavaScriptで取得するには、`document.getElementById`を使います。

```js
// script.js
let element = document.getElementById('example');
console.log(element);
```

これは、`example`というIDを持つ要素を取得して、`element`という変数に保存しています。

また、取得した要素のテキストを取得するには、`innerText`プロパティを使います。

```js
// script.js
let element = document.getElementById('example');
console.log(element.innerText);
```

#### HTML要素を変更する

取得した要素のテキストを変更するには、`innerText`プロパティに新しい値を代入します。

```js
// script.js
let element = document.getElementById('example');
element.innerText = 'こんばんは';
```

このコードを実行すると、`こんにちは`というテキストが`こんばんは`に変わります。

#### CSSを変更する

要素のスタイルを変更するには、`style`プロパティを使います。

```js
// script.js
let element = document.getElementById('example');
let fontSize = 24;
element.style.fontSize = `${fontSize}px`;
```

上のように、フォントサイズなどのスタイルを動的に変更することができます。

また、`classList`プロパティを使うと、CSSのクラスを追加・削除することができとても便利です。

```html
<!-- index.html -->
<p id="example" class="hidden">こんにちは</p>
```

```js
// script.js
let element = document.getElementById('example');
element.classList.remove('hidden'); // hiddenクラスを削除して表示
element.classList.add('text-red-500', 'font-bold', 'text-2xl'); // 複数のクラスを追加
```

#### イベントリスナー

イベントリスナーは、ユーザーの操作（クリック、キーボード入力など）に応じて動作するコードを指定する方法です。

JavaScriptでは、`addEventListener`メソッドを使って、イベントリスナーを登録します。

以下のコードは、ボタンがクリックされたときにアラートを表示するプログラムです。

```html
<!-- index.html -->
<button id="button" class="p-2 text-white font-bold bg-blue-500 rounded-md shadow-md">クリックしてください</button>
```

```js
// script.js
let button = document.getElementById('button');
button.addEventListener('click', () => {
  alert('クリックされました');
});
```

イベントリスナーでは、`click`の他にも、`mouseover`（マウスが要素に乗ったとき）、`keydown`（キーボードが押されたとき）など、様々なイベントを指定することができます。

以下は`keydown`イベントを使ったプログラムです。

```html
<!-- index.html -->
<input id="input" type="text" class="p-2 border-2" />
```

```js
// script.js
let input = document.getElementById('input');
input.addEventListener('keydown', (e) => {
  console.log(e.key);
  if (e.key === 'Enter') {
    alert('Enterが押されました');
  }
});
```

このように`e.key`を使うことで、押されたキーの情報を取得することができます。

---

### ◯チェックポイント

HTMLとJavaScriptの両方を使って、タイピングゲームを少し進化させてみましょう！

まずは以下のコードを準備します。

```html
<!-- index.html -->
<div class="text-center p-5">
  <!-- 問題文 -->
  <p id="question"></p>

  <!-- 入力欄 -->
  <input id="input" class="border-2 mt-3" />
</div>
```

`script.js`を編集して、以下の機能を追加してみましょう。

- 問題を表示する
- 入力された文字が正解かどうかを判定
  - 正解の場合は`score`を1増やす
- 入力欄を空にする
- これを問題数分繰り返す
- 最後の問題まで終わったら、スコアをアラートで表示する
  - 正解数
  - 不正解数
  - 正解率 (%)

かなり難易度が上がってきましたが、これまでのチェックポイントなどを参考にして挑戦してみてください！

詰まったら、まずはヒントを見てみてください。

<details>
<summary>ヒント</summary>

JavaScriptのテンプレートを用意しました！

`// ここに処理を追加`の部分を編集してください。

```js
// script.js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];
let input = document.getElementById('input'); // 入力欄
let questionLabel = document.getElementById('question'); // 問題文
let index = 0; // 問題の番号
let score = 0; // 正解数

questionLabel.innerText = questions[index]; // 1つ目の問題を表示
input.addEventListener('keydown', (e) => {
  if (e.key === 'Enter') {
    // ここに処理を追加
  }
});
```

</details>

<details>
<summary>解答例</summary>

```js
// script.js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];
let input = document.getElementById('input'); // 入力欄
let questionLabel = document.getElementById('question'); // 問題文
let index = 0; // 問題の番号
let score = 0; // 正解数

questionLabel.innerText = questions[index]; // 1つ目の問題を表示
input.addEventListener('keydown', (e) => {
  // Enterが押されたとき
  if (e.key === 'Enter') {
    // 入力された文字が正解かどうか
    if (input.value === questions[index]) {
      score++; // 正解数を1増やす
    }
    input.value = ''; // 入力欄を空にする
    index++; // 次の問題へ

    // 問題が残っているかどうか
    if (index < questions.length) {
      questionLabel.innerText = questions[index]; // 次の問題を表示
    } else {
      let output = `正解数: ${score}
不正解数: ${questions.length - score}
正解率: ${(score / questions.length) * 100}%`;
      alert(output); // スコアを表示
    }
  }
});
```

</details>
