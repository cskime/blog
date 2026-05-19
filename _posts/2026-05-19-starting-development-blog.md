---
title: "Minimal Mistakes로 개발 블로그 시작하기"
date: 2026-05-19 14:45:00 +0900
categories:
  - blog
tags:
  - jekyll
  - github-pages
  - minimal-mistakes
---

GitHub Pages와 Jekyll, Minimal Mistakes 테마로 개발 블로그를 시작했습니다.

이 블로그는 개발 과정에서 배운 내용과 문제를 해결한 기록을 꾸준히 남기기 위한 공간입니다. 반복해서 찾아보게 되는 설정, 라이브러리 사용법, 트러블슈팅 과정을 글로 정리해 두면 다음 작업에서 더 빠르게 판단할 수 있습니다.

## 로컬 실행

의존성을 설치한 뒤 Jekyll 서버를 실행합니다.

```bash
bundle install
bundle exec jekyll serve --livereload
```

브라우저에서 `http://localhost:4000/blog/`로 접속하면 로컬 블로그를 확인할 수 있습니다.

## 배포

이 저장소는 GitHub Pages용 사용자 사이트 저장소입니다. `main` 브랜치에 푸시하면 GitHub Actions가 Jekyll 사이트를 빌드하고 Pages에 배포합니다.
