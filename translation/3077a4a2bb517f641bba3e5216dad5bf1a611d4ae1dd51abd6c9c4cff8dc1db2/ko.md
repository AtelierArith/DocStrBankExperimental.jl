```
@githash_str -> AbstractGitHash
```

주어진 문자열로부터 git 해시 객체를 생성하며, 문자열이 40개의 16진수 숫자보다 짧으면 `GitShortHash`를 반환하고, 그렇지 않으면 `GitHash`를 반환합니다.

# 예제

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
