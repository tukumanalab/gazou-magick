# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# gazou-magick プロジェクトガイド

## プロジェクト概要
画像マジック（Gazou Magick）は、ブラウザ上で動作するシンプルな画像加工ツールです。すべての処理はクライアントサイドで実行され、サーバーへのデータ送信は行いません。

## プロジェクト構成
- `index.html`: メインアプリケーション（単一ファイルで完結）
  - 画像処理機能：背景透過、白黒反転、左右反転
  - SVG→PDF変換機能
- `README.md`: プロジェクトの説明とライセンス情報（MIT License）
- `.clinerules`: Cline用の開発ルール

## アーキテクチャ
- **単一HTMLファイル構成**: すべての機能が`index.html`に含まれる
- **インラインCSS/JS**: 外部ファイル依存を最小限に
- **外部ライブラリ**: 
  - jsPDF (2.5.1): PDF生成
  - svg2pdf.js (2.2.0): SVG→PDF変換
- **処理フロー**:
  1. ファイル選択 → ファイルタイプ判定（PNG/SVG）
  2. 適切なオプションを有効化
  3. リアルタイムプレビュー（Canvas使用）
  4. 加工済みファイルのダウンロード

## 開発ルール

### コードスタイル
- インデント: 2スペース
- セミコロン: 常に使用
- CSS: `<style>`タグ内に記述
- JavaScript: `<script>`タグ内に記述（外部jsファイルなし）
- 命名規則: 分かりやすい英語のクラス名・ID名
- イベントハンドラ: 関数式で定義
- コメント: 日本語で記述
- エラーハンドリング: try-catch使用、console.logとalertで通知

### Git運用
- タスク開始前: mainブランチで`git pull`実行
- 作業: フィーチャーブランチを作成（`feature/機能名`）
- PR作成: `git push`後に`gh pr create`
- ドキュメント: README.mdの更新も同時に行う

### 開発時の注意点
- ファイルが存在しない`svg2pdf.html`への参照がCLAUDE.md内にあるが、現在は未実装
- 画像処理は`processImage()`関数で一元管理
- ダウンロードファイル名は加工内容を反映（例: `filename-transparent-inverted.png`）

## 言語
- 必ず日本語で応対すること
- UIテキスト、エラーメッセージ、コメントはすべて日本語