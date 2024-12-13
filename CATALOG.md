# カタログ

タイピングゲームの追加要素のアイディアをまとめたカタログです。

難易度、かかる時間の目安を★で表現しています。(★~★★★)

## 問題を増やす (★)

問題を増やすだけでも、ゲームとしての質が向上します！

ぜひいろいろな問題を追加してみましょう。

## 背景に模様を追加する (★)

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

## リトライボタンを追加する (★★)

## ベストスコアを保存する (★★)

## 連続タイピング数を導入する (★★)

## タイピング速度を導入する (タイマー機能がある場合) (★★)

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
