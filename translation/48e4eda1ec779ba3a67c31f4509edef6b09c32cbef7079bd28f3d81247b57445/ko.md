```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

`files`로 지정된 경로의 모든 파일을 인덱스 `idx`(또는 `repo`의 인덱스)에서 업데이트합니다. 인덱스의 각 파일 상태를 디스크의 현재 상태와 일치시켜, 디스크에서 제거된 경우 제거하고, 객체 데이터베이스에서 해당 항목을 업데이트합니다.
