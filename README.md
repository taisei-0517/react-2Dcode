# react-2Dcode

QR コード / Aztec コード / DataMatrix の **生成（エンコード）** と **読み取り（デコード）**
がブラウザ上でできる Web アプリです。React + TypeScript 製。

## 機能

### 生成（Generate）
- **QR コード**: テキスト（最大 150 文字）から生成。誤り訂正レベル（L / M / Q / H）、
  サイズ、クワイエットゾーン、前景色・背景色をカスタマイズ可能
- **Aztec コード**: テキストから生成。誤り訂正（5〜90）、サイズを指定可能
- **DataMatrix**: テキストから生成

### 読み取り（Decode）
- QR / Aztec / DataMatrix の画像を読み取ってテキストを表示
- 画像は **ドラッグ＆ドロップ** または **ファイル選択** で入力

## 技術スタック

- [React](https://react.dev/) 19 / TypeScript
- [react-router-dom](https://reactrouter.com/) — 画面遷移
- [qrcode](https://www.npmjs.com/package/qrcode) — QR 生成
- [bwip-js](https://github.com/metafloor/bwip-js) — Aztec / DataMatrix 生成
- [@zxing/browser](https://github.com/zxing-js/browser) — 各コードの読み取り
- [Create React App](https://create-react-app.dev/)（react-scripts）

## 必要環境

- Node.js 16 以上
- npm

## セットアップと実行

```bash
# 依存関係のインストール
npm install

# 開発サーバを起動（http://localhost:3000）
npm start

# 本番ビルド（build/ に出力）
npm run build
```

## 使い方

1. 画面上部のメニューから種類（QR Code / Aztec Code / DataMatrix）を選ぶ
2. **Generate** … テキストとオプションを入力してボタンを押すとコードが表示される
3. **decode** … 画像をドラッグ＆ドロップ、またはファイル選択すると読み取り結果が表示される

## ディレクトリ構成

```
src/
├── App.tsx              画面遷移（ルーティング）とメニュー
├── QR/
│   ├── Encode.tsx       QR 生成
│   └── Decode.tsx       QR 読み取り
├── Aztec/
│   ├── Encode.tsx       Aztec 生成
│   └── Decode.tsx       Aztec 読み取り
└── DataMatrix/
    ├── Encode.tsx       DataMatrix 生成
    └── Decode.tsx       DataMatrix 読み取り
```

生成は種類ごとにライブラリが異なり（QR は qrcode、Aztec / DataMatrix は bwip-js）、
読み取りは共通して @zxing/browser を使っています。
