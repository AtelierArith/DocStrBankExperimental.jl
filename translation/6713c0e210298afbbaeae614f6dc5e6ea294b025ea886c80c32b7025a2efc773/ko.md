```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

`repo`의 인덱스(또는 `repo`의 인덱스)에서 `files`로 지정된 경로의 모든 파일을 제거합니다.
