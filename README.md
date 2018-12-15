# Introduction

## Gitbook 설치
출처: https://beomi.github.io/2017/11/20/Deploy-Gitbook-to-Github-Pages/
```sh
npm install gitbook-cli -g
gitbook init gitbook_init
```

## publish_gitbook.sh
gh-pages 브랜치에 push 할 실행 파일을 생성
```sh
# github pages가 바라보는 gh-pages 브랜치를 만든다.
git checkout gh-pages

# master에서 commit된 내역을 받아 온다.
git merge master

# gitbook 의존 파일을 설치하고 gitbook 빌드를 돌린다.
gitbook install && gitbook build

# 최신 gh-pages 브랜치 정보를 가져와 rebase를 진행한다.
# git pull origin gh-pages --rebase

# gitbook build로 생긴 _book폴더 아래 모든 정보를 현재 위치로 가져온다.
cp -R _book/* .

# node_modules폴더와 _book폴더를 지워준다.
git clean -fx node_modules
git clean -fx _book

# NOQA
git add .

# 커밋커밋!
git commit -a -m "Update docs"

# gh-pages 브랜치에 PUSH!
git push origin -u gh-pages

# 다시 master 브랜치로 돌아온다.
git checkout master

```

## Git 초기화
```sh
git init
git add .
git commit -m "init"
git remote add origin https://...
git branch gh-pages
```

## gh-pages 브랜치에 올리기
```sh
chmod 707 publish_gitbook.sh
./publish_gitbook.sh
```

## 확인
https://유저이름.github.io/레포명/index.html
