---
layout: post
title: "Jekyll과 GitHub Pages로 블로그 만들기"
date: 2025-09-07 12:35:42 +0900
categories: jekyll blog
---

## Jekyll 설치 및 설정

1. Ruby 설치 및 버전 설정
   ```bash
   # 1. `chruby`와 `ruby-install` 설치
   $ brew install chruby ruby-install

   # 2. ruby v3.4.1 설치
   $ ruby-install ruby 3.4.1

   # 3. chruby 사용 설정
   $ echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
   $ echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
   $ echo "chruby ruby-3.4.1" >> ~/.zshrc # run 'chruby' to see actual version
   ```
2. Jekyll 설치
   ```bash
   $ gem install jekyll bundler
   ```
3. Jekyll site 생성
   ```bash
   $ jekyll new myBlog
   ```
4. Jekyll site 실행
   ```bash
   # 변경된 content 자동 반영을 위해 `serve` 명령에  `--livereload` option 추가
   $ jekyll serve --livereload
   ```

## GitHub Pages Hosting

1. GitHub에 `<username>.github.io` repository 생성
2. **[Settings] - [Code and automation] - [Pages]**에서 ‘Build and deployment’의 ‘Source’를 ‘GitHub Actions’로 설정
3. GitHub Actions에서 Jekyll GitHub Pages workflow 추가 ([workflow](https://github.com/cskime/cskime.github.io/blob/main/.github/workflows/jekyll-gh-pages.yml))
4. Local repository에 git을 초기화하고 `<username>.github.io`로 push

## Trouble Shooting

### Minima theme의 `@import` 등 deprecated API warning

![image1](/assets/jekyll-blog/image1.png)
![image2](/assets/jekyll-blog/image2.png)
![image3](/assets/jekyll-blog/image3.png)
![image4](/assets/jekyll-blog/image4.png)
![image5](/assets/jekyll-blog/image5.png)
![image6](/assets/jekyll-blog/image6.png)

- Versions
  - jekyll v4.4.1
  - minima v2.5.2
- Solution
  - 버전 호환을 위해 deprecated API를 당장 교체하지는 않을 것이라고 함 ([GitHub issue](https://github.com/jekyll/minima/issues/815))
  - 최근에는 버전 대응을 위해 작업중인 것 같다.
  - `_config.yaml`에서 `sass:quiet_deps:true` 설정으로 warning을 끌 수 있다.
    ```yaml
    sass:
      quiet_deps: true
    ```
  - 하지만, `@import`에서 발생하는 모든 error를 끄지는 못하는 것 같다..

### 'Platform :mingw, :x64_mingw, :mswin' deprecated warning

![image7](/assets//jekyll-blog/image7.png)

- `Gemfile`에서 `:mingw, :x64_mingw, :mswin` 부분을 `:windows`로 변경
- 또는, windows 환경이 아니라면 주석 처리해도 될 듯

## 참고

- [Jekyll - Jekyll on macOS](https://jekyllrb.com/docs/installation/macos/)
- [Jekyll - Quickstart](https://jekyllrb.com/docs/)
- [Jekyll - GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Jekyll - Posts](https://jekyllrb.com/docs/posts/)
- [GitHub - Setting up a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
