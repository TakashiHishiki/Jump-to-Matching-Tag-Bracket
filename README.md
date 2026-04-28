# Jump to Matching Tag / Bracket

[![Version](https://img.shields.io/visual-studio-marketplace/v/colscenery.jump-to-match-tag?label=Marketplace)](https://marketplace.visualstudio.com/items?itemName=colscenery.jump-to-match-tag)
[![Installs](https://img.shields.io/visual-studio-marketplace/i/colscenery.jump-to-match-tag)](https://marketplace.visualstudio.com/items?itemName=colscenery.jump-to-match-tag)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE.txt)

開きタグ・閉じタグ、または対応するブラケット（括弧）へ、ショートカット一発でジャンプ＆往復できる Visual Studio Code 拡張機能です。  
HTML / Twig / JSX / TSX / TypeScript / PHP / CSS など幅広い言語に対応しています。

---

## Features

- **タグジャンプ** — 開きタグ・閉じタグのどこにカーソルがあっても、ショートカット一発で対応するタグへジャンプ
- **ブラケットジャンプ** — `{` `}` / `(` `)` / `[` `]` の対応する括弧へジャンプ
- **文字列・コメントを賢く無視** — 文字列リテラル・テンプレートリテラル・コメント内の括弧は誤検知しない
- **TypeScript 安全対応** — 純粋な `.ts` / `.js` ファイルではタグ解析をスキップし、TypeScript のジェネリクス（`Array<T>`）や型アサーション（`<Type>value`）を誤検知しない
- **ジャンプ先の一時ハイライト** — カーソルが移動した場所を一瞬強調表示するので、どこに飛んだか一目でわかる
- **右クリックメニュー対応** — エディターの右クリックメニュー（ナビゲーション）からも実行可能

---

## Installation

VS Code の Quick Open（`Ctrl+P` / `Cmd+P`）を開き、以下を貼り付けて Enter を押します。

```
ext install colscenery.jump-to-match-tag
```

または [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=colscenery.jump-to-match-tag) から直接インストールできます。

---

## Keyboard Shortcut

| プラットフォーム | デフォルトショートカット |
|:---:|:---:|
| Windows / Linux | `Ctrl+M` |
| macOS | `Cmd+M` |

**File > Preferences > Keyboard Shortcuts** でコマンド `jumpToMatch.jump` にお好みのキーを割り当て直せます。

---

## Supported Languages

| カテゴリ | 対応言語 |
|---|---|
| HTML 系 | HTML, Twig, XML, PHP, Blade, Vue, Markdown |
| JSX / TSX | JSX, JavaScriptReact, TSX, TypeScriptReact |
| ブラケットのみ | JavaScript, TypeScript, CSS, SCSS, Sass, Less, JSON, JSONC |

---

## Settings

| 設定 | 型 | デフォルト | 説明 |
|---|---|:---:|---|
| `jumpToMatch.highlightMatch` | `boolean` | `true` | ジャンプ後に移動先を一時ハイライトする |
| `jumpToMatch.highlightDurationMs` | `number` | `800` | ハイライトの表示時間（ミリ秒） |

---

## How It Works

1. タグまたは括弧の上（中）にカーソルを置く
2. ショートカット（`Ctrl+M` / `Cmd+M`）を押す
3. 対応するタグまたは括弧へカーソルがジャンプし、移動先が一時ハイライトされる
4. **もう一度押す**と元の位置へ戻る

---

## TypeScript / JavaScript について

純粋な `.ts` / `.js` ファイルではタグ解析を意図的に無効にしています。  
これにより、TypeScript 固有の構文を誤って「タグ」と解釈しません。

```ts
// タグガードがなければ誤検知してしまう例（これらはタグではない）
const arr: Array<string> = [];
const x = <MyType>someValue;
```

`.ts` / `.js` でもブラケットマッチングは正常に動作します。  
タグマッチングは `.tsx` / `.jsx` で完全に有効です。

---

## Release Notes

### 0.4.0
- TypeScript: `.ts` / `.js` でタグ解析を無効化（ジェネリクス・型アサーションの誤検知を防止）
- JS/TS のブラケットマッチングで、文字列・テンプレートリテラル・コメント内の括弧を無視するよう改善
- ユーザー向けテキストを英語に統一
- 拡張機能アイコンを追加

### 0.3.0
- JS/TS の文字列・コメントマスク処理を追加し、ブラケットマッチングの精度を向上
- 純粋な `.js` / `.ts` ファイルでタグ解析を無効化

### 0.2.0
- CSS / SCSS / JSON などへのブラケットマッチングを追加
- ジャンプ先の一時ハイライト機能を追加
- 右クリックコンテキストメニューへのコマンド追加

### 0.1.0
- 初回リリース（HTML タグジャンプ機能）

---

## License

[MIT](./LICENSE.txt)
