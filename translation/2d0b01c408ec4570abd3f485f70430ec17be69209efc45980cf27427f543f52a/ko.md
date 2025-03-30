```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

현재 HEAD로 빠른 병합 변경 사항을 적용합니다. 이는 `ann`이 참조하는 커밋이 현재 HEAD에서 파생된 경우에만 가능합니다(예: 로컬 브랜치 끝보다 단순히 앞서 있는 원격 브랜치에서 변경 사항을 가져오는 경우).
