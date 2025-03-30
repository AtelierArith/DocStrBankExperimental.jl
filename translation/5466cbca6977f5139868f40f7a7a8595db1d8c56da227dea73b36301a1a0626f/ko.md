```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

주석이 달린 커밋(`[`GitAnnotated`](@ref)` 객체로 캡처됨) `anns`의 변경 사항을 저장소 `repo`의 HEAD에 병합합니다. `fastforward`가 `true`인 경우, *오직* 패스트 포워드 병합만 허용됩니다. 이 경우, 충돌이 발생하면 병합이 실패합니다. 그렇지 않으면, `fastforward`가 `false`인 경우, 병합은 사용자가 해결해야 할 충돌 파일을 생성할 수 있습니다.

키워드 인수는 다음과 같습니다:

  * `merge_opts::MergeOptions = MergeOptions()`: 병합을 수행하는 방법에 대한 옵션으로, 패스트 포워딩이 허용되는지 여부를 포함합니다. 자세한 내용은 [`MergeOptions`](@ref)를 참조하십시오.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: 체크아웃을 수행하는 방법에 대한 옵션입니다. 자세한 내용은 [`CheckoutOptions`](@ref)를 참조하십시오.

`anns`는 원격 또는 로컬 브랜치 헤드를 참조할 수 있습니다. 병합이 성공하면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다(예: 브랜치에 공통 조상이 없기 때문에 병합이 불가능한 경우).

# 예제

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# 브랜치를 병합하고, 패스트 포워드
LibGit2.merge!(repo, [upst_ann_1], true)

# 병합 충돌!
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# 브랜치를 병합하고, 패스트 포워드를 시도
LibGit2.merge!(repo, [upst_ann_2], true) # false를 반환합니다
LibGit2.merge!(repo, [upst_ann_2], false) # true를 반환합니다
```
