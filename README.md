# Deep Interview 日本語版

これは [devbrother2024/skills](https://github.com/devbrother2024/skills) の `deep-interview` skill を日本語化し、Codex plugin として配布しやすい形にしたリポジトリです。

原作は DevBrother によるものです。このリポジトリは原作の所有権を主張するものではなく、日本語ローカライズ版として配布するためのものです。

## Quickstart

Codex では、このリポジトリを plugin marketplace として追加したあと、Codex の plugin browser からインストールできます。

```bash
codex plugin marketplace add toru93/deep-interview
```

その後、Codex を開いて `/plugins` を実行し、`Deep Interview` plugin をインストールしてください。

```bash
codex /plugins
```

更新が必要な場合は marketplace を更新します。

```bash
codex plugin marketplace upgrade deep-interview
```

## Skill

| Skill | 説明 | ファイル |
| --- | --- | --- |
| [`deep-interview`](skills/deep-interview/SKILL.md) | 曖昧な依頼をすぐに実行せず、一問ずつ質問して実行可能な要件に整理する Codex skill | `skills/deep-interview/SKILL.md` |

## 目的

AI コーディングエージェントの成果は、モデル性能だけでなく、要件をどれだけ明確に定義できているかに大きく左右されます。

しかし、最初から完璧なプロンプトを書くのは難しいものです。ユーザー自身も、まだ何を求めているのか整理できていない場合があります。

`deep-interview` はこの問題を逆から解きます。AI にすぐ実行させるのではなく、AI が先にユーザーへインタビューし、目的、範囲、制約、完了基準を明確にします。

## 使うタイミング

- アイデアはあるが、要件がまだ曖昧なとき
- Plan Mode に入る前に、文脈をもう少し整理したいとき
- コーディング、プロダクト企画、コンテンツ企画、業務自動化など、成果物の成功基準を先に合わせたいとき

質問は一度に一つだけ行い、各質問は次の構造に従います。

```md
現在の理解: {依頼を一文で要約}
詰まっている決定: {もっとも重要な不確実性}
推奨回答: {あれば提示}
質問: {一つの質問}
```

次の項目が整理できたら、インタビューを終了します。

- 達成したい目的
- 含める範囲と除外する範囲
- 守るべき制約
- 完了判断基準
- まだ残っている未解決の質問

## 手動インストール

plugin marketplace を使わず、直接コピーしても構いません。

Codex グローバルインストール:

```bash
mkdir -p ~/.agents/skills
cp -R skills/deep-interview ~/.agents/skills/deep-interview
```

Codex プロジェクトインストール:

```bash
mkdir -p .agents/skills
cp -R skills/deep-interview .agents/skills/deep-interview
```

インストール後、Codex アプリでは command menu から **Force Reload Skills** を実行するか、アプリを再起動してください。Codex CLI では新しいセッションを開始してください。

## Repository Structure

```text
.
├── .agents/plugins/marketplace.json
├── .codex-plugin/plugin.json
├── skills/deep-interview/SKILL.md
├── LICENSE
├── NOTICE.md
└── README.md
```

## Credits

- Original work: [devbrother2024/skills](https://github.com/devbrother2024/skills)
- Original author: DevBrother
- This repository: Japanese localization and Codex plugin packaging of the original `deep-interview` skill

## License

MIT. See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md).
