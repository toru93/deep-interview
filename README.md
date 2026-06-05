# Deep Interview

Codex가 러프한 요청을 바로 실행하지 않고, 사용자에게 한 번에 하나씩 질문하면서 목표, 범위, 제약, 완료 기준을 구체화하도록 만드는 Codex skill입니다.

사용자에게 보여주는 질문과 요약은 사용자가 쓰는 언어에 맞춥니다. 한국어로 요청하면 한국어로, 일본어로 요청하면 일본어로, 영어로 요청하면 영어로 인터뷰합니다.

日本語版: [README.ja.md](README.ja.md)

## Quickstart

Codex에서는 이 저장소를 plugin marketplace로 추가한 뒤, Codex의 plugin browser에서 설치할 수 있습니다.

```bash
codex plugin marketplace add toru93/deep-interview
```

그다음 Codex를 열고 `/plugins`를 실행한 뒤, `Deep Interview` marketplace에서 `Deep Interview` plugin을 설치하세요.

```bash
codex /plugins
```

업데이트가 필요하면 marketplace를 갱신합니다.

```bash
codex plugin marketplace upgrade deep-interview
```

이 저장소는 `toru93/deep-interview`로 배포됩니다.

## Skills

| Skill | 설명 | 파일 |
| --- | --- | --- |
| [`deep-interview`](skills/deep-interview/SKILL.md) | 러프한 요청을 바로 실행하지 않고, 한 번에 하나씩 질문하여 요구사항을 구체화하는 Codex skill | `skills/deep-interview/SKILL.md` |

## Why This Exists

AI 코딩 에이전트의 결과물 차이는 모델 성능보다 요구사항을 얼마나 명확히 정의했는지에서 크게 갈립니다.

문제는 처음부터 완벽한 프롬프트를 쓰기 어렵다는 점입니다. 사용자 본인도 아직 무엇을 원하는지 모르는 경우가 많기 때문입니다.

`deep-interview`는 이 문제를 역으로 풉니다. AI에게 바로 실행을 맡기기 전에, AI가 먼저 사용자를 인터뷰하게 만들어 목표, 범위, 제약, 완료 기준을 명확하게 만듭니다.

## deep-interview

사용 시점:

- 아이디어는 있지만 요구사항이 흐릿할 때
- Plan Mode로 바로 들어가기 전에 맥락을 더 정리하고 싶을 때
- 코딩, 제품 기획, 콘텐츠 기획, 업무 자동화처럼 결과물의 성공 기준을 먼저 맞춰야 할 때
- 영어, 한국어, 일본어 등 사용자의 언어에 맞춰 인터뷰를 진행하고 싶을 때

사용하지 않을 때:

- 이미 파일, 함수, 변경 범위, 완료 기준이 명확할 때
- 단순 오타 수정, 작은 설정 변경, 좁은 테스트 추가처럼 질문이 오히려 지연을 만들 때
- 사용자가 명시적으로 질문 없이 바로 실행하라고 했을 때

질문은 한 번에 하나만 묻고, 매 질문은 아래 구조를 따릅니다.

```md
현재 이해: {요청을 한 문장으로 요약}
막힌 결정: {가장 중요한 불확실성}
추천 답안: {있으면 제시}
질문: {한 가지 질문}
```

영어 사용자에게는 `Current understanding`, `Blocked decision`, `Recommended answer`, `Question`처럼 라벨을 영어로 바꿉니다. 일본어 사용자에게는 `現在の理解`, `詰まっている決定`, `推奨回答`, `質問`처럼 바꿉니다.

다음 항목이 정리되면 인터뷰를 멈춥니다.

- 달성하려는 목표
- 포함 범위와 제외 범위
- 지켜야 할 제약
- 완료 판단 기준
- 아직 남은 열린 질문

## Manual Install

plugin marketplace를 쓰지 않고 직접 복사해도 됩니다.

Codex 전역 설치:

```bash
mkdir -p ~/.agents/skills
cp -R skills/deep-interview ~/.agents/skills/deep-interview
```

Codex 프로젝트 설치:

```bash
mkdir -p .agents/skills
cp -R skills/deep-interview .agents/skills/deep-interview
```

설치 후 Codex 앱에서는 command menu에서 **Force Reload Skills**를 실행하거나 앱을 재시작하세요. Codex CLI에서는 새 세션을 시작하면 됩니다.

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

README 구조와 설치 안내 흐름은 [devbrother2024/skills](https://github.com/devbrother2024/skills)를 참고했습니다.

## License

MIT
