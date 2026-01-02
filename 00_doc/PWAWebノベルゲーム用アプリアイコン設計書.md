# PWA 化仕様書（HTML 単体 → PWA）

## 対象

- 既存の `index.html` が 1 枚存在する Web サイト
- フレームワーク不使用（HTML / CSS / JS）
- Android（Chrome）を主対象
- HTTPS 配信（Vercel / Netlify / GitHub Pages）

---

## PWA 化に必要な構成要素

### 必須ファイル

| ファイル      | 役割                             |
| ------------- | -------------------------------- |
| index.html    | エントリーポイント               |
| manifest.json | アプリ定義                       |
| sw.js         | Service Worker（キャッシュ制御） |

---

## 製作フロー定義

### STEP 1

- ルート直下に `manifest.json` を追加

### STEP 2

- ルート直下に `sw.js` を追加

### STEP 3

- `index.html` に以下を追加
  - manifest 読み込み
  - Service Worker 登録処理

### STEP 4

- HTTPS 環境にデプロイ
- Android Chrome でインストール確認

---

## フォルダー構造定義

### 最小構成（PWA 成立条件）

/ ├─ index.html ├─ manifest.json ├─ sw.js └─ icons/ ├─ icon-192.png └─ icon-512.png
