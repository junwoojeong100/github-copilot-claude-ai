---
applyTo: "**"
description: "Git 워크플로우 지침. 커밋 메시지 언어, 브랜치 전략, PR 생성 규칙을 포함합니다."
---

# Git 워크플로우 지침

## 커밋 메시지

### 언어: 영어 고정
- **모든 커밋 메시지는 영어로 작성합니다.** (대화 언어가 한국어여도 동일)
- 사용자와의 대화는 한국어를 유지하되, 커밋 메시지 본문·제목·설명은 영어로 통일합니다.

### 형식: Conventional Commits
- 제목은 `type(scope): short summary` 형태를 기본으로 합니다.
  - 주요 type: `feat`, `fix`, `docs`, `refactor`, `chore`, `test`, `style`, `perf`, `ci`, `build`
- 제목은 명령형(imperative mood), 72자 이내, 마침표 없이 작성합니다.
- 본문이 필요한 경우 제목과 빈 줄로 구분하고, 변경 이유(why)와 영향 범위를 설명합니다.

### Co-authored-by 트레일러
모든 커밋 메시지 끝에 아래 트레일러를 반드시 포함합니다:

```
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
```

### 예시

```
docs: refine README title to reflect kit purpose

Rename the top-level heading so it aligns with the repository name
and conveys the kit's purpose at a glance.

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
```

## 브랜치 전략

- `main` 브랜치에 **직접 푸시하지 않습니다.**
- 변경 사항은 항상 새 브랜치에서 작업합니다.
- 브랜치명은 kebab-case로, 앞에 타입 프리픽스를 붙입니다:
  - `feat/<short-topic>`, `fix/<short-topic>`, `docs/<short-topic>`, `chore/<short-topic>` 등

## Pull Request

### 항상 PR 생성
- 변경 사항을 푸시한 뒤에는 **항상 `main` 브랜치를 base로 하는 PR을 생성합니다.**
- PR 생성은 `gh pr create --base main --head <branch>` 를 사용합니다.
- 단일 커밋의 단순 변경이라도 PR을 건너뛰지 않습니다. 사용자가 명시적으로 "PR 없이 바로 머지"를 요청한 경우에만 예외로 합니다.

### PR 제목과 본문
- **PR 제목은 영어**로, 관련 커밋 제목과 동일한 Conventional Commits 형식을 따릅니다.
- **PR 본문도 영어**로 작성하며, 아래 섹션을 기본 구조로 합니다:

```markdown
## Summary
What changed and why, in one or two sentences.

## Changes
- Bullet list of concrete changes (files / areas touched).

## Notes
Anything reviewers should know (risk, rollout, follow-ups).
```

### 머지 정책
- 머지 방식(merge/squash/rebase)은 리포 기본 설정을 따릅니다.
- 사용자가 명시적으로 요청하기 전까지 에이전트가 직접 PR을 머지하지 않습니다.
