<p align="center"><img src="docs/banner.png" alt="유튜브 게시 점검: 썸네일·고정 댓글 확인 전에는 완료가 아닙니다" width="100%"></p>

<p align="center">
<a href="https://github.com/reedodev/youtube-publish-checklist/actions/workflows/test.yml"><img src="https://github.com/reedodev/youtube-publish-checklist/actions/workflows/test.yml/badge.svg" alt="test"></a>
<img src="https://img.shields.io/badge/Claude_Code-skill-2547F4" alt="Claude Code skill">
<img src="https://img.shields.io/badge/license-MIT-black" alt="MIT">
</p>

# 유튜브 게시 점검 (youtube-publish-checklist)

롱폼과 쇼츠마다 맞춤 썸네일(규격·용량·채널 표시)과 고정 댓글을 확인하고, 예약 공개라면 공개 뒤 댓글을 달 후속 작업이 있는지까지 검사합니다. 하나라도 빠지면 '게시 완료'라고 보고하지 못하게 합니다.

<!-- prereq-adapt -->
## 무엇이 필요한가요?

꼭 필요한 것은 Node 18 이상, 영상마다 만든 맞춤 썸네일 파일, YouTube Studio 접근(브라우저)입니다. 권장·선택 준비물까지 정리한 표는 [SKILL.md의 준비물](skills/youtube-publish-checklist/SKILL.md#준비물-쓰기-전에-있어야-하는-것)에 있습니다.

## 바꿔 쓰기

에이전트에게 다음처럼 말하면 옵션을 바꿔서 실행합니다.

- "아동용 영상이라 댓글이 없어" → `publish.json`에서 그 영상에 `"madeForKids": true`
- "이 영상은 고정 댓글 안 달 거야" → `"skipPinnedComment": true` (사용자가 직접 정한 경우만)
- "썸네일만 먼저 검사해 줘" → `publish-gate.mjs thumb thumb.jpg --kind short`

말과 옵션의 대응표는 [SKILL.md의 바꿔 쓰기](skills/youtube-publish-checklist/SKILL.md#바꿔-쓰기-이렇게-말하세요)에 있습니다.

## 설치

**Claude Code 플러그인으로 설치**

```
/plugin marketplace add reedodev/youtube-publish-checklist
/plugin install youtube-publish-checklist@youtube-publish-checklist
```

**폴더만 복사**

```bash
git clone https://github.com/reedodev/youtube-publish-checklist.git
cp -r youtube-publish-checklist/skills/youtube-publish-checklist ~/.claude/skills/
```

필요한 것: Node 18+

## 바로 해 보기

```bash
node skills/youtube-publish-checklist/scripts/publish-gate.mjs thumb thumb.jpg --kind long
node skills/youtube-publish-checklist/scripts/publish-gate.mjs check publish.json
```

자세한 절차, 옵션, 한계는 [SKILL.md](skills/youtube-publish-checklist/SKILL.md)에 있습니다. 에이전트가 이 파일을 읽고 그대로 따릅니다.

## 시험

`node tests/run.mjs`가 SKILL.md 형식을 검사하고 예시 파일로 스크립트를 실제로 실행합니다. 푸시할 때마다 GitHub Actions가 같은 시험을 돌립니다(위 test 배지).

## 만든 사람

**리도**, AI 좌충우돌 실습 중인 20년차 엔지니어입니다. 매일 AI에게 일을 맡기다가 막힌 부분을 고쳐 가며 이 스킬을 만들었습니다.
[YouTube @Reedodev](https://www.youtube.com/@Reedodev) · [Threads @reedo.dev](https://www.threads.com/@reedo.dev) · [GitHub @reedodev](https://github.com/reedodev)

같이 만든 다른 스킬: [옵시디언 3D 지식그래프](https://github.com/reedodev/obsidian-brain-3d) · [노트 먼저 찾아보기](https://github.com/reedodev/vault-recall) · [작업 기록 강의자료](https://github.com/reedodev/work-to-lecture-deck) · [한국어 말투 점검](https://github.com/reedodev/korean-tone-check) · [네이버 황금키워드](https://github.com/reedodev/naver-golden-keywords) · [한글 양식 채우기](https://github.com/reedodev/hwpx-form-fill) · [TTS 끝소리 고치기](https://github.com/reedodev/tts-tail-fix) · [카드뉴스 렌더](https://github.com/reedodev/html-card-render) · [영상 비율 검사](https://github.com/reedodev/social-video-gate)

---

## English

Per-video publish gate for YouTube: custom thumbnail (size, ratio, shown on channel) and pinned comment, including a required follow-up task for scheduled releases.

Install: `/plugin marketplace add reedodev/youtube-publish-checklist` then `/plugin install youtube-publish-checklist@youtube-publish-checklist`, or copy `skills/youtube-publish-checklist` into `~/.claude/skills/`. See [SKILL.md](skills/youtube-publish-checklist/SKILL.md) for the full procedure. MIT License; third-party models, fonts and libraries keep their own licenses.
