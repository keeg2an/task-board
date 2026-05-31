# task-board

タスク管理ボードアプリケーションのプロジェクトです。

## Git 運用ルール

### コード変更のたびに GitHub へプッシュする

コードを変更するたびに、以下の手順でコミットおよびプッシュを行うこと。

```
git add <変更ファイル>
git commit -m "コミットメッセージ"
git push origin <ブランチ名>
```

- コミットは機能単位・修正単位でまとめる（無関係な変更を混在させない）
- コミットメッセージは変更内容が分かるように具体的に書く
- `main` ブランチへの直接プッシュは避け、作業ブランチ → プルリクエスト経由でマージする
- ブランチ名の例: `feature/タスク追加機能`, `fix/バグ修正`

### ブランチ戦略

- `main`: 本番相当のブランチ。直接コミット禁止
- `feature/*`: 新機能開発
- `fix/*`: バグ修正
- `chore/*`: 設定変更・リファクタリングなど

### コミットメッセージの形式

```
<種別>: <概要>

例:
feat: タスク追加フォームを実装
fix: タスク削除時のエラーを修正
chore: 依存パッケージをアップデート
```

## デプロイ先

- **GitHub Pages**: https://keeg2an.github.io/task-board/
- `master` ブランチへのプッシュで GitHub Actions が自動ビルド・デプロイ
- ワークフロー定義: `.github/workflows/deploy.yml`

## 技術スタック

| 種別 | 技術 |
|---|---|
| UI ライブラリ | React 18 |
| ビルドツール | Vite 6 |
| 言語 | JavaScript (JSX) |
| スタイリング | Plain CSS (CSS Modules 未使用) |
| 状態管理 | React `useState` / `useEffect` |
| データ永続化 | `localStorage` |
| パッケージマネージャ | npm |
| CI/CD | GitHub Actions |

## コンポーネント命名規約

- コンポーネントファイル名・関数名は **PascalCase** （例: `App`, `TaskItem`）
- ファイル拡張子は `.jsx`
- 1ファイル1コンポーネントを基本とする
- CSSクラス名は **kebab-case** （例: `.task-item`, `.add-button`, `.board-title`）
- `localStorage` のキーは **kebab-case** の定数で管理（例: `task-board-tasks`）

## 開発ルール

- 変更前にかならず `git status` で現在の状態を確認する
- プッシュ前にはテスト・動作確認を行う
- セキュリティに関わる情報（APIキー、パスワードなど）は絶対にコミットしない（`.env` を `.gitignore` に追加する）
