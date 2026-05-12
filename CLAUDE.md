# CLAUDE.md

このファイルはClaude Codeがこのプロジェクトで作業する際のガイドラインを定義します。

## プロジェクト概要

React製のシンプルなタスクボードアプリ。タスクの追加・完了トグル・削除が可能で、データはlocalStorageに永続化される。

## デプロイ先

https://anna0521.github.io/task-board/

GitHub Actions（`.github/workflows/deploy.yml`）により、`main`ブランチへのpush時に自動デプロイされる。

## 技術スタック

| カテゴリ | 技術 |
|---|---|
| UIフレームワーク | React 19 |
| ビルドツール | Vite 8 |
| 言語 | JavaScript (JSX) |
| スタイリング | プレーンCSS（`App.css`, `index.css`） |
| 状態管理 | React組み込みフック（`useState`, `useEffect`） |
| データ永続化 | localStorage |
| デプロイ | GitHub Pages + GitHub Actions |

## Git運用ルール

### コード変更時のプッシュ義務

**コードを変更するたびに、必ずGitHubにプッシュすること。**

具体的な手順：

1. 変更をステージングに追加する
   ```
   git add <変更ファイル>
   ```

2. コミットメッセージを作成してコミットする
   ```
   git commit -m "変更内容の要約"
   ```

3. GitHubにプッシュする
   ```
   git push origin <ブランチ名>
   ```

### コミットメッセージの規則

- 日本語または英語で記述する
- 変更の「何を」「なぜ」変えたかが分かるメッセージにする
- 1行目に要約（50文字以内推奨）、必要なら2行目以降に詳細を記載する

例：
```
ユーザー認証機能を追加

- JWTトークンによるセッション管理を実装
- ログイン・ログアウトAPIを追加
```

### ブランチ戦略

- `main` / `master`: 本番用の安定ブランチ
- `feature/<機能名>`: 新機能開発用
- `fix/<バグ名>`: バグ修正用

### 注意事項

- `.env` や認証情報が含まれるファイルは絶対にコミットしない
- `main` / `master` への直接プッシュは避け、プルリクエストを経由すること
- force push（`git push --force`）は原則禁止

## コーディング規則

### コンポーネントの命名規約

- **ファイル名**: PascalCase（例: `TaskItem.jsx`, `AddTaskForm.jsx`）
- **コンポーネント関数名**: ファイル名と同じPascalCase
- **CSSクラス名**: ケバブケース（例: `task-list`, `input-row`, `delete`）
- **イベントハンドラ**: `handle` プレフィックス（例: `handleKeyDown`, `handleSubmit`）
- **状態変数**: camelCase の名詞（例: `tasks`, `input`）
- **状態セッター**: `set` + 状態変数名のPascalCase（例: `setTasks`, `setInput`）

### ファイル構成

```
src/
├── App.jsx          # アプリのルートコンポーネント
├── App.css          # App固有のスタイル
├── main.jsx         # エントリーポイント
├── index.css        # グローバルスタイル
└── assets/          # 画像などの静的ファイル
```

新規コンポーネントを追加する場合は `src/components/` ディレクトリを作成してそこに配置する。

## 開発環境のセットアップ

（セットアップ手順をここに記載してください）
