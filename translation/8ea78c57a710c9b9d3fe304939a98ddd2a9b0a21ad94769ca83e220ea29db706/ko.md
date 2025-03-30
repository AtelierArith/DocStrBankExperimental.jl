```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

`ConfigEntry`를 다음 조각으로 나눕니다: 섹션, 하위 섹션, 이름, 값.

# 예시

다음과 같은 git 구성 파일이 주어졌을 때:

```
[credential "https://example.com"]
    username = me
```

`ConfigEntry`는 다음과 같이 보일 것입니다:

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

자세한 내용은 [git config 구문 문서](https://git-scm.com/docs/git-config#_syntax)를 참조하세요.
