# 범용적으로 사용할 수 있는 tailwind-aa-theme

## hugo project를 시작합니다. (v0.85.0)

```bash
hugo version
hugo new site {PROJECTNAME}
cd {PROJECTNAME}
git init
```

## tailwind-aa-theme를 hugo 프로젝트 themes 폴더에 추가합니다.

```bash
cd HUGO_SITE_DIR/themes
git submodule add https://github.com/team-durumi/tailwind-aa-theme
git commit -m "submodule add tailwind-aa-theme"
git submodule update --init --recursive
```

## config.toml 파일에 hugo 기본 설정을 저장합니다. 
- stats are used by the CSS purging
- 최초 생성한 휴고 프로젝트에는 디자인에 사용된 content, data, static 경로가 비어있기 때문에 module.mounts를 지정합니다.
- simple search 관련 요소가 레이아웃에 포함되어 오류시 hugo-search-fuse-js 테마를 추가하면 됩니다.

```toml
baseURL = "https://PROJECTNAME.durumi.io"
languageCode = "ko-kr"
title = "PROJECTNAME"
theme = "tailwind-aa-theme"

[build]
writeStats = true

[module]

  [[module.mounts]]
    source = "themes/tailwind-aa-theme/exampleSite/content"
    target = "content"  

  [[module.mounts]]
    source = "themes/tailwind-aa-theme/exampleSite/data"
    target = "data"    

  [[module.mounts]]
    source = "themes/tailwind-aa-theme/exampleSite/static"
    target = "static"
```

## hugo 프로젝트 최상위 폴더로 돌아와서 npm 설치합니다.
```bash
hugo mod npm pack
npm install
hugo server -D
```
- node module package를 설치합니다.
- .gitignore 파일에 node_modules / resources / public 폴더를 추가합니다.

## Site를 구성 - contents 에 맞는 목록과 layout을 적용합니다. 
- marketing 영역에서 블로그(post)를 추가합니다. 임시로 아이템목록을 뿌려놓습니다.
- 변경되는 자료나 레이아웃을 업데이트하면서 사이트를 확인합니다. 
```bash
hugo server -F --cleanDestinationDir
```

## 메뉴샘플 & Taxonomy
- 헤더 메뉴와 바로 연결됩니다. 
```toml
[menu]

  [[menu.main]]
  name = "Home"
  URL = "/"
  weight = 1

  [[menu.main]]
  name = "File Browse"
  URL = "items"
  weight = 2

  [[menu.main]]
  name = "Search"
  URL = "search"
  weight = 3
```
- 사용하는 Taxonomy의 종류에 따라 이를 지정해 줍니다. 
```toml
[taxonomies]
  tag = "tags"
  subject = "subjects"
  creator = "creators"
  venue = "venues"
  source = "sources"
```

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

## tailwind-aa-theme의 변경사항을 가져옵니다. 
- 변경된 부분에 대해 해당 프로젝트에서도 기록을 남겨야 netlify 까지 잘 반영됩니다. 

```bash
git submodule foreach git pull origin master
```


# Data

## items record management
- ```exampleSite/content/items``` 폴더를 content 폴더에 복사해서 item에 해당하는 유형을 정리합니다. (소규모)
- 공유된 자료폴더(Google Drive)의 items 폴더를 ```content/items``` 로 Sync 혹은 심볼릭링크를 겁니다. 

## 심볼릭링크
```symlink
ln -s  /Volumes/GoogleDrive/공유\ 드라이브/kctu-photo/items {{경로}}/hugo/kctu-photo/content
```

```unlink
unlink items
```

## ExampleSite의 폴더를 hugo 폴더로 복제하고 사용자 정보를 업데이트합니다. 

- data/marketing.yml
- data/slider.json


# Build(SSG)

- Develop-build는 cloudflare 연결이 쉽도록 pages를 사용해봅니다. 
- Prodcution-build netlify로 연결합니다. (변경해도 됩니다.)
- netlify 배포시 오류가 날 때 환경변수 build version을 직접 적용합니다.

```toml
[build]
publish = "public"
command = "hugo --gc --minify -d public;"

[context.production.environment]
HUGO_VERSION = "0.81.0"
```

# 기타

## netlify CMS
- https://www.netlifycms.org/docs/hugo/#creating-a-new-site 앞 부분은 스킵
- ```static/admin``` 폴더에 index.html과 config.yml 을 추가합니다. (git-gateway 를 수정하지 않는다.)
- Front 경로 접근할 때 Netlify Identity를 확인할 수 있는 스크립트도 반드시 추가한다. 
- items는 depth가 있어서 md file을 모두 인식하지 못 함. (post로 변경)

## hugo-debugprint를 추가해서 변수를 확인합니다.

```bash
cd HUGO_SITE_DIR/themes
git submodule add https://github.com/kaushalmodi/hugo-debugprint
git submodule update --init --recursive
```