```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}; kwargs...) -> Bool
```

주석이 달린 커밋(`[`GitAnnotated`](@ref) 객체로 캡처됨)`anns`의 변경 사항을 저장소`repo`의 HEAD에 병합합니다. 키워드 인수는 다음과 같습니다:

  * `merge_opts::MergeOptions = MergeOptions()`: 병합을 수행하는 방법에 대한 옵션으로, 패스트 포워딩이 허용되는지 여부를 포함합니다. 자세한 내용은 [`MergeOptions`](@ref)를 참조하십시오.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: 체크아웃을 수행하는 방법에 대한 옵션입니다. 자세한 내용은 [`CheckoutOptions`](@ref)를 참조하십시오.

`anns`는 원격 또는 로컬 브랜치 헤드를 참조할 수 있습니다. 병합이 성공하면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다(예: 브랜치에 공통 조상이 없기 때문에 병합이 불가능한 경우).

# 예제

```julia
upst_ann = LibGit2.GitAnnotated(repo, "branch/a")

# 브랜치를 병합합니다.
LibGit2.merge!(repo, [upst_ann])
```
