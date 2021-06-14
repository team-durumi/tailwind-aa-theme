# 범용적으로 사용할 수 있는 tailwind-aa-theme

## hugo project를 시작합니다. 

```bash
hugo new site {PROJECTNAME}
git init

```

## tailwind-aa-theme를 hugo 프로젝트 themes 폴더에 추가합니다.

```bash
cd HUGO_SITE_DIR/themes
git submodule add https://github.com/team-durumi/tailwind-aa-theme
git commit -m "submodule add tailwind-aa-theme"
git submodule update --init --recursive
```
hugo 프로젝트 최상위 폴더로 돌아와서
```bash
hugo mod npm pack
npm install
hugo server -D
```

You need to add this to your `config.toml` (the stats are used by the CSS purging):

```toml
[build]
writeStats = true
```
- node module package를 설치합니다. 
- config.toml의 사이트 정보를 변경합니다. 
- node module package를 설치합니다. 
- .gitignore 파일에 node_modules / resources / public 폴더를 추가합니다. 
- netlify.toml 파일에서 build version을 확인합니다.


## ExampleSite의 폴더를 hugo 폴더로 복제하고 사용자 정보를 업데이트합니다. 

- data/marketing.yml
- data/slider.json

## tailwind-aa-theme의 변경사항을 가져옵니다. 
- 변경된 부분에 대해 해당 프로젝트에서도 기록을 남겨야 netlify 까지 잘 반영됩니다. 

```bash
git submodule foreach git pull origin master
```

## 헤더메뉴/푸터메뉴 
- theme.toml 파일에 있는 메뉴 설정을 config.toml 파일에 지정합니다. 
```
theme.toml
```

## hugo-debugprint를 추가해서 변수를 확인합니다.

```bash
cd HUGO_SITE_DIR/themes
git submodule add https://github.com/kaushalmodi/hugo-debugprint
git submodule update --init --recursive
```

## contents 에 맞는 목록과 layout을 적용합니다. 
- marketing 영역에서 블로그(post)를 추가합니다. 임시로 아이템목록을 뿌려놓습니다.

## Simple Search
- https://github.com/kaushalmodi/hugo-search-fuse-js
- submodule로 복사하고, 테마를 설정합니다. ```theme = ["hugo-search-fuse-js", "my-theme"]```
- search.md 를 content 폴더에 추가합니다. 
- aa 테마 ```layouts/_default/search.html``` 을 복사해서 프로젝트 layout에 지정해주세요. 

```
+++
title = "Search"
layout = "search"
outputs = ["html", "json"]
[sitemap]
  priority = 0.1
+++
```

## netlify CMS
- https://www.netlifycms.org/docs/hugo/#creating-a-new-site 앞 부분은 스킵
- ```static/admin``` 폴더에 index.html과 config.yml 을 추가합니다. (git-gateway 를 수정하지 않는다.)
- Front 경로 접근할 때 Netlify Identity를 확인할 수 있는 스크립트도 반드시 추가한다. 
- items는 depth가 있어서 md file을 모두 인식하지 못 함. (post로 변경)

## items record management
- ```exampleSite/content/items``` 폴더를 content 폴더에 복사해서 item에 해당하는 유형을 정리합니다. 
