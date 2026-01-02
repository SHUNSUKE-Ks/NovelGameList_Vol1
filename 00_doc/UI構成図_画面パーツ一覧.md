# UI構成図・画面パーツ一覧

本ドキュメントでは、`NovelGame01_vol1` プロジェクトにおける画面構成、各セクション、および主要なUIパーツについて定義します。
開発者およびデザイナー間の共通言語（ナレッジ）として利用してください。

## 画面一覧 (Screens)

| 画面ID | 画面名 | 役割 |
| :--- | :--- | :--- |
| `TITLE` | タイトル画面 | ゲームの起動画面。スタートボタンのみ配置。 |
| `CHAPTER_GALLERY` | チャプター選択画面 | エピソードおよびチャプターを選択し、開始するイベントを選ぶ画面。 |
| `MAIN` | メインゲーム画面 | ノベルパートの進行画面。背景、立ち絵、メッセージウィンドウを表示。 |
| `RESULT` | リザルト画面 | シナリオ終了後の結果表示画面。 |

---

## 画面詳細 (Screen Details)

### 1. タイトル画面 (TITLE)
クラス名: `.title-screen`

*   **コンテナ**: `.title-content` - コンテンツの中央揃え用ラッパー
*   **タイトルロゴ**: `.game-title` - ゲームタイトル「理の魔法使い」を表示
*   **アクション**: `.start-button` - 「始める」ボタン。押下でチャプター選択画面へ遷移。

### 2. チャプター選択画面 (CHAPTER_GALLERY)
クラス名: `.chapter-gallery-screen`

この画面は大きく「サイドパネル」と「メインコンテンツエリア」に分かれています。

#### A. サイドパネル (Side Panel)
クラス名: `.side-panel`
左側に配置され、エピソードとチャプターの一覧を表示するためのナビゲーションエリアです。

*   **開閉ボタン**: `.toggle-panel-btn` - パネルの表示/非表示を切り替えるボタン（◀ / ▶）。
*   **ヘッダー**: `.side-panel-header` > `.side-panel-title` - 「目次」というタイトルを表示。
*   **リストコンテナ**: `.stepper-container` - エピソードリストを格納するスクロール領域。
    *   **エピソード項目**: `.episode-item`
        *   **エピソードタイトル**: `.episode-header` - 例：「Episode 1: 理の探求」
        *   **チャプターリスト**: `.chapter-list`
            *   **チャプター項目**: `.chapter-item` - クリック可能なチャプター名。選択中は `.active` クラスが付与される。

#### B. メインコンテンツエリア (Main Content Area)
クラス名: `.main-content-area`
右側に配置され、選択中のチャプター詳細とイベント一覧を表示します。

*   **タイトルセクション**: `.chapter-title-section`
    *   **サブタイトル**: `.chapter-subtitle` - エピソード名を表示。
    *   **メインタイトル**: `.chapter-main-title` - チャプター名を表示。
*   **イベントグリッド**: `.events-grid` - イベントカードを並べるグリッドレイアウト。
    *   **イベントカード**: `.event-card` - 個別のイベント（ストーリー）を表すカード。
        *   **イベント名**: `.event-title`
        *   **説明文**: `.event-description`
        *   **読むボタン**: `.event-read-btn` - ストーリーを開始するボタン。

### 3. メインゲーム画面 (MAIN)
クラス名: `.main-game-screen`

*   **背景レイヤー**: `.background-layer` - 背景画像を表示（例: `.bg-magic-tower`, `.bg-black`）。
*   **キャラクターレイヤー**: `.character-layer` - 立ち絵を表示するエリア。
    *   **キャラクタースプライト**: `.character-sprite` - 個別のキャラクターアイコン。
*   **メッセージウィンドウ**: `.message-window` - 画面下部のテキスト表示エリア。
    *   **話者名**: `.speaker-name` - 発言者の名前。
    *   **メッセージ**: `.message-text` - タイプライターエフェクトで表示されるテキスト。
    *   **ページ送りアイコン**: `.next-indicator` - テキスト表示完了時に表示される「▼」マーク。
*   **選択肢コンテナ**: `.choice-container` - 選択肢発生時に表示されるエリア。
    *   **選択肢ボタン**: `.choice-button` - 個別の選択肢。

### 4. リザルト画面 (RESULT)
クラス名: `.result-screen`

*   **コンテナ**: `.result-content`
*   **タイトル**: `.result-title` - 「真理への道」や「エンディング」などを表示。
*   **メッセージ**: `.result-message` - 結末に応じたテキストを表示。
*   **戻るボタン**: `.return-button` - 「チャプター選択に戻る」ボタン。

---

## 開発メモ

*   **HTMLファイル**: `index.html` - 全画面の構造が記述されています。
*   **CSSファイル**: `style.css` - 上記クラス名のスタイルが定義されています。
*   **状態管理**: `gameState` オブジェクト内の `screen` プロパティによって、描画する画面関数（`renderTitleScreen`, `renderChapterGallery`など）を切り替えています。
