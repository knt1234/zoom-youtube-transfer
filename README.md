# Zoom → YouTube 自動転送ツール

Zoomのクラウド録画を、指定した期間まとめてYouTubeへ自動アップロードするGoogle Colabノートブックです。

## 特徴

- **完全無料** — Google Colab・Zoom・YouTubeの無料枠内で動作
- **Googleドライブの容量を消費しない** — アップロード完了後に一時ファイルを自動削除
- **ノーコード** — フォームに入力してボタンを押すだけで転送完了
- **セキュア** — APIキーはあなた自身のGoogleアカウント内にのみ保存

## 使い方

### 1. ノートブックをColabで開く

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/knt1234/zoom-youtube-transfer/blob/main/zoom_youtube_transfer.ipynb)

### 2. API設定（初回のみ）

ノートブック内の「② API設定ガイド」セクションに詳しい手順が記載されています。

#### Zoom の設定
1. [Zoom App Marketplace](https://marketplace.zoom.us/) で **Server-to-Server OAuth** アプリを作成
2. `Account ID` / `Client ID` / `Client Secret` を取得
3. Colabの左メニュー「🔑 シークレット」に以下を登録
   - `ZOOM_ACCOUNT_ID`
   - `ZOOM_CLIENT_ID`
   - `ZOOM_CLIENT_SECRET`

#### YouTube の設定
1. [Google Cloud Console](https://console.cloud.google.com/) で **YouTube Data API v3** を有効化
2. OAuthクライアントID（デスクトップアプリ）を作成し `client_secrets.json` をダウンロード
3. ノートブック実行時にそのファイルをアップロード

> **注意：** 15分以上の動画をアップロードするには、YouTubeアカウントの[電話番号認証](https://www.youtube.com/verify)が必要です。

### 3. ノートブックを実行

1. `③ セットアップ` セルを実行（ライブラリのインストール）
2. `④ 転送設定` フォームで期間・公開設定・タイトルを入力
3. `⑤ 転送実行` セルを実行 → 自動で転送が始まります

## 制限事項

| 項目 | 制限 |
|------|------|
| YouTube APIの1日あたり上限 | 約6件（10,000ユニット/日） |
| 動画の長さ | 15分以上は事前に電話番号認証が必要 |
| ファイル形式 | MP4のみ対応（Zoomのクラウド録画はMP4で保存されます） |

## セキュリティについて

- `client_secrets.json` や `*.pkl`（認証トークン）は `.gitignore` で除外されており、リポジトリにはアップロードされません
- ColabのシークレットはGoogleアカウントに紐付けられており、他者から参照できません

## ライセンス

MIT
