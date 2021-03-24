## content/sample-aa

### dropbox에 있는 Sample-item을 콘텐츠 폴더로 옮깁니다. 로컬 폴더에 있는 정리되지 않은 파일을 dropbox로 옮깁니다.
```
$ rclone sync dropbox:/items/aa /Users/woonjjang/hugo/tailwind-aa/content/items/aa
$ rclone sync /Users/woonjjang/hugo/tailwind-aa/content/items/aa dropbox:/items/aa 
```

### hugo content 폴더에서 목적을 가지고, 해당 폴더를 분류합니다. 기존에 분류가 되어 있다면, 폴더채로 옮겨올 수 있습니다. 
- 분류한 이후에 동기화를 했더니, dropbox의 목록이 그대로 유지됩니다. 
- dropbox에서 공동으로 편집할 것인지, 깃을 활용해 편집할 것인지 판단이 필요합니다. 
- (맥에서 편집한 폴더명의 에러)해당 폴더와 아이템 자체를 인지하지 못 해서 생기는 문제였음. 

$ rclone sync dropbox:/aa /Users/woonjjang/dev/ccwps/content/aa
$ rclone sync /Users/woonjjang/dev/ccwps/content/items dropbox:/items 