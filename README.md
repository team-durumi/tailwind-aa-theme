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
- .gitignore 파일에 node_modules / resources / publc 폴더를 추가합니다. 
- netlify.toml 파일에서 build version을 확인합니다.


## ExampleSite의 폴더를 hugo 폴더로 복제하고 사용자 정보를 업데이트합니다. 

- data/marketing.yml
- data/slider.json

## tailwind-aa-theme의 변경사항을 가져옵니다. 
- 변경된 부분에 대해 해당 프로젝트에서도 기록을 남겨야 netlify 까지 잘 반영됩니다. 

```bash
git submodule foreach git pull https://github.com/team-durumi/tailwind-aa-theme.git
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