```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

git 저장소 `repo`의 각 파일 상태에 대한 정보를 수집합니다(예: 파일이 수정되었는지, 스테이징되었는지 등). `status_opts`는 추적되지 않은 파일을 볼지 여부나 서브모듈을 포함할지 여부와 같은 다양한 옵션을 설정하는 데 사용할 수 있습니다. 자세한 내용은 [`StatusOptions`](@ref)를 참조하십시오.
