# human-ai-cognition-lab.github.io

Human-AI Cognition Lab의 공개 연구 사이트를 GitHub Pages에 배포하기 위한 껍데기 레포입니다. 이 레포에는 콘텐츠나 빌드 코드가 없습니다 — CI가 [research-book](https://github.com/human-ai-cognition-lab/research-book)을 체크아웃해서 [mdBook](https://rust-lang.github.io/mdBook/)으로 직접 빌드하고 배포합니다.

글 작성/수정은 항상 `research-book`에서 합니다. 이 레포는 건드릴 일이 거의 없습니다.

## 로컬 미리보기

이 레포가 아니라 `research-book`에서 `mdbook serve`를 실행하세요.

## 배포

`research-book`의 `main` 브랜치에 push되면 → repository_dispatch로 이 레포의 `.github/workflows/deploy.yml`이 트리거되어, `research-book`을 체크아웃하고 `mdbook build` 후 GitHub Pages에 배포합니다. 이 레포 자체에 push하거나 수동 실행(`workflow_dispatch`)해도 재배포됩니다.

### 최초 1회 수동 설정 필요

`research-book` → 이 레포로의 즉시 트리거(repository_dispatch)를 위해, `research-book` 레포에 이 레포에 대한 dispatch 권한을 가진 Personal Access Token을 `SITE_DISPATCH_TOKEN`이라는 이름의 secret으로 등록해야 합니다. (fine-grained PAT: 이 레포에 대한 Contents 읽기/쓰기 권한, 또는 classic PAT: `repo` scope)
