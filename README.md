# QMS フロー図エディタ

QMS（品質管理システム）文書のフロー図を作成・編集するためのHTMLベースのエディタです。  
Google Apps Script の `javascript.html` に貼り付けて使用します。

## 機能

- **左右分割レイアウト**: 左にSVGコードエディタ、右にリアルタイムプレビュー
- **図形テンプレート挿入**: ツールバーのボタンでQMS標準図形をワンクリック挿入
- **リアルタイムプレビュー**: コード編集に連動してプレビューが即時更新
- **ドラッグ分割バー**: 左右パネルの幅をドラッグで調整
- **SVGコピー**: ワンクリックでSVGコード全体をクリップボードにコピー

## 対応図形

| カテゴリ | 図形 | 説明 |
|---------|------|------|
| 基本 | 開始/終了 | 角丸長方形 |
| 基本 | プロセス | 長方形 |
| 基本 | 判断 | ひし形 |
| 基本 | 矢印 | 接続線（矢印マーカー付き） |
| 拡張 | 書類 | 波型下辺の長方形 |
| 拡張 | データベース | 円柱形 |
| 拡張 | 入出力 | 平行四辺形 |
| 拡張 | 手動操作 | 台形 |
| 拡張 | 定義済処理 | 二重線入り長方形 |
| 拡張 | スイムレーン | ヘッダー付き区画 |

## GAS への貼り付け手順

1. [script.google.com](https://script.google.com) でスタンドアロン型プロジェクトを作成
2. `ファイル` > `新規作成` > `HTML` で `javascript` という名前のファイルを作成
3. `javascript.html` の内容をすべてコピーして貼り付ける
4. `Code.gs` に以下の `doGet()` 関数を記述
5. `デプロイ` > `新しいデプロイ` > 種類: `ウェブアプリ` を選択してデプロイ
6. 発行されたURLにアクセスしてエディタを使用

```javascript
// Code.gs（ウェブアプリとしてデプロイ）
function doGet() {
  return HtmlService.createHtmlOutputFromFile('javascript')
    .setTitle('QMS フロー図エディタ')
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}
```

## ローカルでの確認

ブラウザで `javascript.html` を直接開くことで動作確認できます。

## ファイル構成

```
qms_flow/
├── javascript.html      # メインHTML（GASに貼り付ける本体）
├── README.md            # このファイル
└── examples/
    └── sample_flow.svg  # サンプルフロー図
```
