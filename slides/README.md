# 登壇スライド

コーディングエージェント入門セミナー（今日は無料の OpenCode × OpenRouter で体験）の登壇資料です。

- 成果物: [`seminar.pptx`](./seminar.pptx)（全26枚 / 16:9 ワイド）
- 生成元: [`generate.js`](./generate.js)（[PptxGenJS](https://gitbrent.github.io/PptxGenJS/) でコードから生成）

## 再生成する

Node.js が必要です。

```sh
cd slides
npm install
npm run build   # generate.js を実行して seminar.pptx を出力
```

このリポジトリは Nix を使うため、Node.js が無い場合は次でも実行できます。

```sh
nix shell nixpkgs#nodejs_22 --command bash -c 'npm install && npm run build'
```

## 構成

| 章 | 内容 | スライド |
|----|------|----------|
| Intro | コーディングエージェントとは / 代表的なエージェント / なぜターミナル・OpenCode・OpenRouter / 全体図 | 1–10 |
| Setup | ターミナル準備 / OpenCode インストール | 11–12 |
| Connect | API キー作成 / フォルダを作って起動 / `/connect` / Free Models Router | 13–16 |
| Build | 使い方 / ToDoアプリを作る / プロンプト / ローカルサーバーで確認 / 指示ファイル / レート制限 | 17–22 |
| Wrap up | 振り返り / 応用 / 参考リンク | 23–26 |

## ねらい・方針

- **コーディングエージェントの本質は「手元の PC を直接操作できる」こと**（ファイルの読み書き＋コマンド実行）。これが Web チャット（コピペ）との決定的な違いで、slide5「とは」で中心に据える。複数ファイルを扱えるのはこの能力の一例で、それ自体を本質として大きく扱わない。
- **プロンプトはシンプルに**。「作りたいもの」と「こうなってほしい」だけ伝え、ファイル名や分け方の指定はしない（どう作るかはエージェントに任せる＝自律感）。
- **ハンズオンは ToDo アプリ**。`python3 -m http.server`（→ `localhost:8000`）でブラウザ確認。ES Modules は `file://` では動かないため。Node は不要で、サーバー起動もエージェントに頼める。
- **初心者向けに余計な説明を削ぐ**。git・環境変数・`command not found`・「なぜ Router か」などは扱わない。
- **特定ツールに依存しすぎない**。実習は無料の OpenCode だが、「代表的なエージェント」「指示ファイル（AGENTS.md / CLAUDE.md）」「参考リンク」を横断的に扱い、Claude Code / Codex CLI ユーザーにも通用する内容にしている。

## 実機検証メモ

実際に opencode へスライドのプロンプトを投げて確認済み（`openrouter/free` ルーター経由で ToDo アプリが生成できた）。

- TUI で「Free Models Router」を選ぶ前提なので、スライド本文には内部モデルIDを出さない（CLI で試す場合の ID は `openrouter/openrouter/free`）。
- 無料・軽量モデルは一度の指示で全ファイルが揃わないことがある（最後の1ファイルを説明だけして書かない等）。その場合は続けてもう一度頼めば補完される。

デザインは GitHub Dark 基調・ターミナルモチーフで統一。日本語は Hiragino Sans、コードは Menlo を前提にしているため、macOS で開くと最も綺麗に表示されます。
