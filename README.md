# 범용적으로 사용할 수 있는 tailwind-aa-theme

## tailwind-aa-theme를 hugo 프로젝트 themes 폴더에 복사합니다. 

To use this theme
```shell
cd HUGO_SITE_DIR/themes
git clone https://github.com/woonjjang/tailwind-aa-theme
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

- config.toml의 사이트 정보를 변경합니다. 
- node module package를 설치합니다. 


## ExampleSite의 폴더를 hugo 폴더로 복제하고 사용자 정보를 업데이트합니다. 

- data/marketing.yml
- data/slider.json