# カタログ

タイピングゲームの追加要素のアイディアをまとめたカタログです。

難易度、かかる時間の目安を★で表現しています。(★~★★★)

## 問題を増やす (★)

問題を増やすだけでも、ゲームとしての質が向上します！

ぜひいろいろな問題を追加してみましょう。

## 背景に模様を追加する (★)

背景を装飾すると、一気にテーマが明確になります。

Tailwind CSSで作成してもいいですが、ここではCSSファイルを新たに作成して見ましょう。

まず、`index.html`と同じ階層に`style.css`を作成します。

そして、`index.html`の`<head>`の中で以下のように`style.css`を読み込みます。

```html
<!-- index.html -->
<head>
  <!-- 省略 -->
  <link rel="stylesheet" href="./style.css">
</head>
```

たとえば、`body`タグに水玉模様を追加する場合は以下のように記述します。

```css
/* style.css */
body {
  background-image: radial-gradient(circle, #dbeafe 5px, transparent 5px),
    radial-gradient(circle, #dbeafe 5px, transparent 5px);
  background-position: 0 0, 15px 30px;
  background-size: 30px 60px;
}
```

これでも良いですが、CSSファイルでは自分でクラスを作ることが一般的です。ドット(`.`)を使ってクラスを指定します。

```css
/* style.css */
.bg_dots {
  background-image: radial-gradient(circle, #dbeafe 5px, transparent 5px),
    radial-gradient(circle, #dbeafe 5px, transparent 5px);
  background-position: 0 0, 15px 30px;
  background-size: 30px 60px;
}
```

```html
<!-- index.html -->
<body class="bg_dots">
  <!-- 省略 -->
</body>
```

きれいな背景パターンを提供しているサイトはたくさんあります。Googleなどで調べるか、以下のサイトを参考にしてみてください。

- [CSSでストライプなどの背景パターンを作る方法](https://tamatuf.net/html-css/css-gradient-stripe/)
- [【CSS】使える背景パターン、実装サンプル25選（コピペで簡単です）](https://125naroom.com/web/3737)
- [コピペでできる！cssとhtmlのみで作るいい感じの背景パターン 12選](https://copypet.jp/2206/)

## 総タイピング数を表示する (★)

タイピングゲームのスコアは、正解数だけでなく総タイピング数も重要です。

問題に正解したときに、その文字列の長さを加算していき、最後に表示するようにしましょう。

文字列の長さは`length`プロパティで取得できます。

```js
let question = 'apple';
let length = question.length;
console.log(length); // 5
```

では、以下のような手順で総タイピング数を表示してみましょう。

- 総タイピング数を保存する変数を用意する(`let total = 0;`など)
- 問題に正解したときに、その文字列の長さを加算する(`total += question.length;`)
- 最後に総タイピング数を表示する

## タイピング速度を導入する (タイマー機能、総タイピング数がある場合) (★)

タイピング速度は、総タイピング数とかかった時間から計算することができます。

`タイピング速度 = 総タイピング数 / 時間`

この機能自体は割り算を使って簡単に実装できますが、タイマーや総タイピング数を先に実装する必要があります。

## 問題をランダムにする (★★)

JavaScriptで乱数を生成することで、問題をランダムに表示することができます。

乱数は`Math.random()`を使って生成します。

```js
let random = Math.random();
console.log(random);
```

また、`Math.floor()`を使って小数点以下を切り捨てることもできます。

```js
let random = Math.floor(Math.random() * 10); // 0以上10未満の乱数
console.log(random);
```

それでは、以下のように`Math.random()`を使ってランダムなインデックスを取得しましょう。

```js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];

let index = Math.floor(Math.random() * questions.length);
let question = questions[index];
```

- `Math.random()`は0以上1未満の乱数を生成します
- `Math.floor()`は小数点以下を切り捨てます
- `Math.random() * questions.length`で0以上`questions.length`未満の乱数を生成します
- `index`が使えなくなるので、現在の出題数を保持する変数を追加しましょう

## 問題が重複しないようにする (ランダムの場合) (★★)

既に出題された問題を管理することで、問題が重複しないようにすることができます。

以下のように、出題された問題を管理する配列を用意し、出題された問題はその配列に追加していきます。

```js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];
let asked = []; // 出題された問題

let index = Math.floor(Math.random() * questions.length);
// すでに出題された問題が出題されるまで乱数を生成
while (asked.includes(index)) {
  index = Math.floor(Math.random() * questions.length);
}
asked.push(index);

let question = questions[index];
```

上のように、`includes()`を使うと、配列に指定した要素が含まれているかを判定することができます。

<details>
<summary>発展</summary>

実は配列ではなく、`Set`というデータ構造があります。

これは重複しないデータを保持するのに特化しており、配列を使うよりも高速に要素の存在を判定できます。

```js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];
let asked = new Set(); // 出題された問題

let index = Math.floor(Math.random() * questions.length);

// すでに出題された問題が出題されるまで乱数を生成
while (asked.has(index)) {
  index = Math.floor(Math.random() * questions.length);
}
asked.add(index);

let question = questions[index];
```

</details>

## 日本語とローマ字を表示する (★★)

配列と`オブジェクト`を組み合わせると、日本語とローマ字の問題を表示することができます。

`オブジェクト`は、キーと値のペアを保持するデータ構造です。

```js
let question = { ja: 'おにぎり', en: 'onigiri' }; // オブジェクト

console.log(question.ja); // おにぎり
console.log(question.en); // onigiri
```

`question.ja`や`question.en`のように、キーを指定することで値を取得できます。

さらに、配列にオブジェクトを格納することで、問題を日本語とローマ字で表示することができるようになります。

```js
let questions = [
  { ja: 'おにぎり', en: 'onigiri' },
  { ja: '唐揚げ', en: 'karaage' },
  { ja: 'たこ焼き', en: 'takoyaki' },
  { ja: 'ラーメン', en: 'ra-menn' },
  { ja: '焼きそば', en: 'yakisoba' },
];

for (let i = 0; i < questions.length; i++) {
  let question = questions[i];
  console.log('日本語: ' + question.ja + ', ローマ字: ' + question.en);
}
```

HTMLに日本語を表示するラベル、ローマ字を表示するラベルの両方を用意し、問題を表示してみましょう。

## リトライボタンを追加する (★★)

リトライボタンを実装するためには、おおまかに以下の手順が必要です。

- リトライボタンを用意する
  - 初期状態では非表示にしておく(`class="hidden"`)
  - 問題が終了したらリトライボタンを表示する
- リトライボタンをクリックしたら、問題をリセットする
  - `addEventListener`を使ってクリックイベントを追加する
  - その中で、点数や問題番号などをリセットする
  - ボタンは再度非表示にする

タイマーなど追加要素を導入している場合は、それらもリセットする必要があります。

## ベストスコアを保存する (★★)

現在の実装では、ブラウザを閉じたりリロードするとスコアがリセットされてしまいます。

これを解決するためには、スコアを保存する仕組みを導入する必要があります。

`localStorage`を使うと、ブラウザにデータを保存することができます。

```js
localStorage.setItem('bestScore', 2); // データを保存
let bestScore = localStorage.getItem('bestScore'); // データを取得
console.log(bestScore); // 2
```

タイピングが終わったときに、現在のスコアとベストスコアを比較し、ベストスコアを更新するようにしましょう。

```js
let score = 5; // 現在のスコア
let bestScore = localStorage.getItem('bestScore'); // ベストスコア

// ベストスコアと現在のスコアを比較し、ベストスコアを更新
if (score > bestScore) {
  localStorage.setItem('bestScore', score);
}
```

ベストスコアを表示するためには、HTMLにベストスコアを表示する要素を用意し、JavaScriptでその要素にベストスコアを表示するようにしましょう。

## 連続タイピング数を導入する (★★)

総タイピング数と似ていますが、連続で正解した回数もゲーム性を高める要素です。

実装手順は以下の通りです。

- 現在の連続タイピング数を保存する変数を用意する
  - 例: `let consecutive = 0;`
- 最大連続タイピング数を保存する変数を用意する
  - 例: `let maxConsecutive = 0;`
- 問題に正解したときに、連続タイピング数を1増やす
  - `consecutive++;`
  - もし連続タイピング数が最大連続タイピング数を超えていたら、最大連続タイピング数を更新する
    ```js
    if (consecutive > maxConsecutive) {
      maxConsecutive = consecutive;
    }
    ```
- 問題に間違えたときに、連続タイピング数をリセットする
  - `consecutive = 0;`
- 最後に最大連続タイピング数を表示する

## スコアの計算方法を変更する (★★)

## 全体的なデザインを変更する (★★)

## Enterキーなしで正誤判定する (★★★)

初期状態だと、Enterキーを押すことで入力が確定しますが、これだとあまりスムーズではありません。

いろいろな実装方法がありますが、ここでは入力を間違えたらその入力をキャンセルする方法で実装してみましょう。

なお、この実装だと正解率が必ず100%になってしまいます。そのため、タイマーなどと組み合わせるとなお良いでしょう。

<details>
<summary>ヒント</summary>

- まず、`if (e.key === 'Enter') {`を削除しましょう
- 現在入力されたキーは`e.key`で取得でき、それ以前の入力は`input.value`に格納されています
  - 入力すべてを取得するには、`let currentInput = input.value + e.key`のようにします
- 現在までの入力が問題文の先頭と一致していなかったら、入力をキャンセルします
  - `questions[index].startsWith(currentInput)`で先頭が一致しているかを確認できます
- 入力のキャンセルは、`e.preventDefault()`で行います

</details>

<details>
<summary>実装例</summary>

```js
let questions = ['apple', 'banana', 'orange', 'grape', 'melon'];
let input = document.getElementById('input'); // 入力欄
let questionLabel = document.getElementById('question'); // 問題文
let index = 0; // 問題の番号
let score = 0; // 正解数

questionLabel.innerText = questions[index]; // 1つ目の問題を表示
input.addEventListener('keydown', (e) => {
  let currentInput = input.value + e.key;

  // 入力が問題文の先頭と一致していない場合
  if (!questions[index].startsWith(currentInput)) {
    e.preventDefault(); // 入力をキャンセル
    return;
  }

  // 入力された文字が正解かどうか
  if (currentInput === questions[index]) {
    e.preventDefault(); // 入力をキャンセルしないと次の問題まで入力が残ってしまう
    score++; // 正解数を1増やす
    input.value = ''; // 入力欄を空にする
    index++; // 次の問題へ
  }

  // 問題が残っているかどうか
  if (index < questions.length) {
    questionLabel.innerText = questions[index]; // 次の問題を表示
  } else {
    let output = `正解数: ${score}
不正解数: ${questions.length - score}
正解率: ${(score / questions.length) * 100}%`;
    alert(output); // スコアを表示
  }
});
```

</details>

## 結果をalertではなく画面に表示する (★★★)

## 音を追加する (★★★)

## タイマー機能を追加する (★★★)

## タイマーゲージを追加する (★★★)

## 問題レベルを導入する (★★★)
