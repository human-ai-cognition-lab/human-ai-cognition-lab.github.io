# human-ai-cognition-lab.github.io

Human-AI Cognition Lab의 공개 연구 사이트 ([Docusaurus](https://docusaurus.io/)). 실제 콘텐츠는 이 레포가 아니라 [research-book](https://github.com/human-ai-cognition-lab/research-book)(mdBook 소스)에서 작성하고, `scripts/sync-content.mjs`가 빌드 시점에 가져와 `docs/`에 반영합니다. `docs/`는 생성물이라 git에 커밋하지 않습니다.

## 로컬 개발

`research-book`이 이 레포와 형제 폴더로 clone되어 있어야 합니다 (기본 경로: `../research-book`).

```
npm install
npm start
```

`npm start`/`npm run build` 실행 전에 `npm run sync`가 자동으로 실행되어 최신 콘텐츠를 가져옵니다.

## 배포

`main` 브랜치 push, `research-book` 업데이트(repository_dispatch), 또는 수동 실행(`workflow_dispatch`) 시 `.github/workflows/deploy.yml`이 빌드 후 GitHub Pages에 배포합니다.

### 최초 1회 수동 설정 필요

`research-book` → 이 레포로의 즉시 트리거(repository_dispatch)를 위해, `research-book` 레포에 이 레포에 대한 dispatch 권한을 가진 Personal Access Token을 `SITE_DISPATCH_TOKEN`이라는 이름의 secret으로 등록해야 합니다. (fine-grained PAT: 이 레포에 대한 Contents 읽기/쓰기 권한, 또는 classic PAT: `repo` scope)
