# CLAUDE.md

## プロジェクト概要

このファイルはClaude Codeがプロジェクトを理解・操作するためのガイドラインです。

---

## Git 運用ルール

### 基本方針

**コードを変更するたびに、必ずGitHubへプッシュすること。**

### 手順

1. **変更後は即コミット＆プッシュ**
   - ファイルを編集・作成・削除した場合、作業が完了次第コミットしてGitHubにプッシュする
   - 「あとでまとめてプッシュ」はしない

2. **コミットメッセージ**
   - 変更内容を端的に日本語または英語で記述する
   - 例: `feat: ユーザー認証機能を追加`, `fix: ログイン時のバリデーションエラーを修正`

3. **プッシュコマンド**
   ```powershell
   git add <変更ファイル>
   git commit -m "メッセージ"
   git push origin <ブランチ名>
   ```

4. **ブランチ戦略**
   - `main` / `master`: 本番相当のコード
   - 機能追加・修正は原則フィーチャーブランチで作業し、完了後にマージする

5. **禁止事項**
   - `--force` プッシュは明示的な指示がない限り禁止
   - `--no-verify` によるフック回避は禁止
   - `.env` や認証情報ファイルのコミットは禁止

---

## デプロイ先

- **GitHub Pages**: https://himagaku02.github.io/task_board/
- `main` ブランチへのプッシュで GitHub Actions が自動ビルド＆デプロイ

---

## 技術スタック

| 種別 | 技術 |
|---|---|
| UI ライブラリ | React 18 |
| ビルドツール | Vite 6 |
| 言語 | JavaScript (JSX) |
| スタイリング | プレーン CSS (CSS Modules 不使用) |
| 状態管理 | React `useState` / `useEffect` |
| 永続化 | `localStorage` |
| CI/CD | GitHub Actions |
| ホスティング | GitHub Pages |

---

## コンポーネント命名規約

- **コンポーネントファイル**: PascalCase（例: `TaskItem.jsx`, `TaskList.jsx`）
- **コンポーネント関数**: PascalCase（例: `export default function TaskBoard()`）
- **CSS クラス名**: kebab-case（例: `.task-item`, `.delete-btn`）
- **イベントハンドラ**: `handle` プレフィックス（例: `handleKeyDown`, `handleSubmit`）
- **状態変数**: camelCase（例: `tasks`, `inputValue`）
- **ファイル配置**: コンポーネントは `src/` 直下に置く（現状は小規模のため）

---

## 開発環境

- **OS**: Windows 11
- **Shell**: PowerShell / Bash
- **作業ディレクトリ**: `c:\Users\himag\Documents\Claude_Work\Claude_Work\DAY2_task`
- **開発サーバー起動**: `npm run dev` → http://localhost:5173

---

## コーディング規約

- コメントは「なぜ」その実装なのかが非自明な場合にのみ記述する
- 不要なコード、デッドコードは残さず削除する
- セキュリティ上のリスク（SQLインジェクション、XSS等）を導入しない

---

## Claude Codeへの指示

- コードを変更したら、ユーザーへの確認なしに `git add` → `git commit` → `git push` を実行してよい
- コミットメッセージには `Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>` を付与する
- プッシュ先はデフォルトの `origin` を使用する
