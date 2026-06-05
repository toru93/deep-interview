---
name: deep-interview
description: |
  Use this skill to turn vague requests into clear, execution-ready requirements through a Socratic interview.
  Trigger when the user asks for deep interview, requirements clarification, thought organization, interview me, don't assume, 심층 인터뷰, 요구사항 명확화, 생각 정리, インタビュー, 要件整理, or when goal, scope, constraints, or acceptance criteria are unclear.
  Do not use for already-specific requests, small typo fixes, narrow configuration changes, or test additions where asking would add little value.
argument-hint: "<rough request>"
---

# Deep Interview

Do not execute an ambiguous request immediately. Turn it into clear requirements first.

The goal is not to ask many questions. The goal is to find the single highest-impact uncertainty and resolve it one step at a time.

Use a Socratic style. Do not decide on behalf of the user. Ask questions that reveal their assumptions, decision criteria, tradeoffs, and boundaries.

## Language And Output

Detect the user's primary language from the current conversation and write all user-facing questions, summaries, recommendations, and final notes in that language.

If the user explicitly requests a language, tone, or output format, follow that request.

If multiple languages are mixed, follow the primary language of the latest user message.

Keep code identifiers, file paths, commands, product names, and error messages in their original form.

Preserve the output structure, but translate labels naturally into the user's language. For example:

```md
Current understanding: {one-sentence summary}
Blocked decision: {the most important unresolved uncertainty}
Recommended answer: {optional recommendation}
Question: {one focused question}
```

For Korean, use labels such as `현재 이해`, `막힌 결정`, `추천 답안`, `질문`.

For Japanese, use labels such as `現在の理解`, `詰まっている決定`, `推奨回答`, `質問`.

## Clarification Axes

Pick the single most unclear axis in this order:

- Goal
- Scope and non-goals
- Constraints
- Acceptance criteria
- Existing context and impact area

If the answer can be discovered from the codebase or available context, inspect it directly instead of asking the user.

## Interview Flow

Ask one question at a time. Each question must include the current understanding, the blocked decision, an optional recommended answer, and one focused question.

Use this structure with labels translated into the user's language:

```md
Current understanding: {summarize the request in one sentence}
Blocked decision: {name the highest-impact uncertainty}
Recommended answer: {offer a practical default if one exists}
Question: {ask one question}
```

After the user answers, briefly update what has been decided. Ask another question only if an important uncertainty remains.

When choices help, provide only 2-3 options and always allow free-form input.

## Stop Criteria

Stop when these are clear enough to act on:

- Goal
- In-scope work and out-of-scope work
- Constraints
- Acceptance criteria
- Remaining open questions

At the end, summarize only the decisions and remaining open questions. Do not recap the entire conversation.
