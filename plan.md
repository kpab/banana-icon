# VSCode バナナアイコン拡張機能 開発計画 🍌

## プロジェクト概要

すべてのファイルタイプをバナナアイコンで統一表示する VSCode 拡張機能の開発

### 目標

- 🎯 すべてのファイル種別をバナナアイコン 🍌 で表示
- 🎯 簡単インストール・設定変更
- 🎯 パフォーマンスに影響を与えない軽量実装

## 技術的実現可能性

### ✅ 完全実装可能

- VSCode の`iconThemes` API を使用
- カスタムアイコンテーマとして実装
- 全ファイル形式への適用が可能

## プロジェクト構造

```
/projects/banana-icons-vscode/
├── package.json              # 拡張機能マニフェスト
├── README.md                 # ドキュメント
├── CHANGELOG.md              # 変更履歴
├── LICENSE                   # ライセンス
├── .gitignore               # Git除外設定
├── .vscodeignore            # VSCode除外設定
├── icons/                   # アイコンリソース
│   ├── banana.svg           # メインバナナアイコン
│   ├── banana-folder.svg    # フォルダ用バナナアイコン
│   └── banana-folder-open.svg # 開いたフォルダ用
├── themes/                  # テーマ定義
│   └── banana-theme.json    # アイコンテーマ設定
└── .vscode/                 # 開発環境設定
    ├── launch.json          # デバッグ設定
    └── settings.json        # プロジェクト設定
```

## 実装フェーズ

### Phase 1: プロジェクト初期化

**タスク:**

1. プロジェクトディレクトリ作成
2. package.json 作成・設定
3. 基本ディレクトリ構造作成
4. Git リポジトリ初期化

**成果物:**

- 基本プロジェクト構造
- 拡張機能マニフェスト

### Phase 2: アイコンデザイン・作成

**タスク:**

1. バナナアイコン SVG デザイン作成
2. 複数サイズ対応（16x16, 24x24）
3. フォルダ用バナナアイコン作成
4. アイコン品質確認

**成果物:**

- banana.svg（ファイル用）
- banana-folder.svg（フォルダ用）
- banana-folder-open.svg（開いたフォルダ用）

### Phase 3: アイコンテーマ実装

**タスク:**

1. banana-theme.json 作成
2. ファイル拡張子マッピング設定
3. デフォルトアイコン設定
4. フォルダアイコン設定

**主要設定項目:**

```json
{
  "iconDefinitions": {
    "banana": { "iconPath": "./icons/banana.svg" }
  },
  "file": "banana",
  "folder": "banana-folder",
  "fileExtensions": {
    "js": "banana",
    "ts": "banana",
    "json": "banana"
    // 全拡張子に適用
  }
}
```

### Phase 4: 拡張機能設定

**タスク:**

1. package.json の完成
2. 拡張機能メタデータ設定
3. contribution points 設定
4. 公開準備

**package.json 主要設定:**

```json
{
  "name": "banana-icons",
  "displayName": "Banana Icons 🍌",
  "description": "すべてのファイルをバナナアイコンで表示",
  "version": "1.0.0",
  "engines": { "vscode": "^1.60.0" },
  "categories": ["Themes"],
  "contributes": {
    "iconThemes": [
      {
        "id": "banana-icons",
        "label": "Banana Icons 🍌",
        "path": "./themes/banana-theme.json"
      }
    ]
  }
}
```

### Phase 5: ドキュメント・テスト

**タスク:**

1. README.md 作成
2. インストール手順記載
3. 使用方法説明
4. ローカルテスト実行

## 技術仕様

### サポート対象

- **VSCode バージョン:** 1.60.0 以上
- **ファイル形式:** 全形式対応
- **OS:** Windows, macOS, Linux

### アイコン仕様

- **形式:** SVG
- **サイズ:** 16x16px（基本）
- **カラー:** フルカラー
- **スタイル:** フラットデザイン

### パフォーマンス考慮

- SVG 形式による軽量化
- 最小限のファイル数
- キャッシュ効率の最適化

## インストール・使用手順

### インストール方法

1. VSCode 拡張機能マーケットプレイスから検索
2. "Banana Icons" をインストール
3. VSCode 再起動

### 設定方法

1. `Ctrl+Shift+P`（Cmd+Shift+P on Mac）
2. "Preferences: File Icon Theme" を実行
3. "Banana Icons 🍌" を選択

### 無効化方法

1. 同様の手順で別のアイコンテーマを選択
2. または "None" を選択してデフォルトに戻す

## 開発スケジュール

| フェーズ | 期間 | 主要マイルストーン       |
| -------- | ---- | ------------------------ |
| Phase 1  | 1 日 | プロジェクト作成完了     |
| Phase 2  | 2 日 | アイコンデザイン完成     |
| Phase 3  | 2 日 | テーマ実装完了           |
| Phase 4  | 1 日 | 拡張機能設定完了         |
| Phase 5  | 1 日 | ドキュメント・テスト完了 |

**総開発期間:** 約 1 週間

## リスク・対策

### 潜在的リスク

1. **アイコンデザインの統一性**

   - 対策: シンプルなデザインガイドライン策定

2. **VSCode API 変更**

   - 対策: 最新 API 仕様の継続確認

3. **パフォーマンス影響**
   - 対策: 軽量 SVG アイコンの使用

## 今後の拡張可能性

### v2.0 機能案

- 🍌 複数バナナテーマ（青バナナ、完熟バナナ等）
- 🍌 アニメーション効果
- 🍌 カスタマイズ可能な色設定
- 🍌 ファイルサイズ表示機能

## まとめ

この計画により、すべてのファイルをバナナアイコンで統一表示する VSCode 拡張機能を効率的に開発できます。シンプルながら実用性の高い拡張機能として、多くのユーザーに愛用される可能性があります。
