# 범용적으로 사용할 수 있는 tailwind-aa-theme

## hugo site에 적용하기 위해 테마만 분리합니다. 


## As a Project

```bash
npm install
hugo server
```

## As a Theme

Import `github.com/bep/hugo-starter-tailwind-basic/v2` (use `github.com/bep/hugo-starter-tailwind-basic` if you want/need Tailwind 1.x.) into your project, and then run:

```bash
hugo mod npm pack
npm install
```

You need to add this to your `config.toml` (the stats are used by the CSS purging):

```toml
[build]
writeStats = true
```