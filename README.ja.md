# Deep Interview

Codex が曖昧な依頼をすぐに実行せず、ユーザーに一問ずつ質問しながら、目的、範囲、制約、完了基準を具体化する Codex skill です。

ユーザーに表示する質問と要約は、ユーザーが使っている言語に合わせます。日本語で依頼された場合は日本語で、韓国語で依頼された場合は韓国語で、英語で依頼された場合は英語でインタビューします。

한국어판: [README.md](README.md)

## Quickstart

Codex では、このリポジトリを plugin marketplace として追加したあと、Codex の plugin browser からインストールできます。

```bash
codex plugin marketplace add toru93/deep-interview
```

その後、Codex を開いて `/plugins` を実行し、`Deep Interview` marketplace から `Deep Interview` plugin をインストールしてください。

```bash
codex /plugins
```

更新が必要な場合は marketplace を更新します。

```bash
codex plugin marketplace upgrade deep-interview
```

このリポジトリは `toru93/deep-interview` として配布されます。

## Skills

| Skill | 説明 | ファイル |
| --- | --- | --- |
| [`deep-interview`](skills/deep-interview/SKILL.md) | 曖昧な依頼をすぐに実行せず、一問ずつ質問して要件を具体化する Codex skill | `skills/deep-interview/SKILL.md` |

## Why This Exists

AI コーディングエージェントの成果は、モデル性能だけでなく、要件をどれだけ明確に定義できているかに大きく左右されます。

しかし、最初から完璧なプロンプトを書くのは難しいものです。ユーザー自身も、まだ何を求めているのか整理できていない場合があります。

`deep-interview` はこの問題を逆から解きます。AI にすぐ実行させるのではなく、AI が先にユーザーへインタビューし、目的、範囲、制約、完了基準を明確にします。

## deep-interview

使うタイミング:

- アイデアはあるが、要件がまだ曖昧なとき
- Plan Mode に入る前に、文脈をもう少し整理したいとき
- コーディング、プロダクト企画、コンテンツ企画、業務自動化など、成果物の成功基準を先に合わせたいとき
- 英語、韓国語、日本語など、ユーザーの言語に合わせてインタビューしたいとき

使わないタイミング:

- ファイル、関数、変更範囲、完了基準がすでに明確なとき
- 単純な誤字修正、小さな設定変更、狭いテスト追加など、質問がむしろ遅延になるとき
- ユーザーが質問なしで直接実行するよう明示しているとき

質問は一度に一つだけ行い、各質問は次の構造に従います。

```md
現在の理解: {依頼を一文で要約}
詰まっている決定: {もっとも重要な不確実性}
推奨回答: {あれば提示}
質問: {一つの質問}
```

韓国語ユーザーには `현재 이해`, `막힌 결정`, `추천 답안`, `질문` のようにラベルを韓国語にします。英語ユーザーには `Current understanding`, `Blocked decision`, `Recommended answer`, `Question` のようにラベルを英語にします。

次の項目が整理できたら、インタビューを終了します。

- 達成したい目的
- 含める範囲と除外する範囲
- 守るべき制約
- 完了判断基準
- まだ残っている未解決の質問

## Manual Install

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
├── README.md
└── README.ja.md
```

## Credits

README の構成とインストール案内の流れは [devbrother2024/skills](https://github.com/devbrother2024/skills) を参考にしました。

## License

MIT
