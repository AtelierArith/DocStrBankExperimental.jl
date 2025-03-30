```
merge!(repo::GitRepo; kwargs...) -> Bool
```

저장소 `repo`에서 git 병합을 수행하여 분기된 이력을 가진 커밋을 현재 브랜치에 병합합니다. 병합이 성공하면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

키워드 인자는 다음과 같습니다:

  * `committish::AbstractString=""`: `committish`에 있는 명명된 커밋을 병합합니다.
  * `branch::AbstractString=""`: 브랜치 `branch`와 현재 브랜치에서 분기된 이후의 모든 커밋을 병합합니다.
  * `fastforward::Bool=false`: `fastforward`가 `true`인 경우, 병합이 패스트 포워드인 경우에만 병합합니다(현재 브랜치 헤드가 병합할 커밋의 조상인 경우). 그렇지 않으면 병합을 거부하고 `false`를 반환합니다. 이는 git CLI 옵션 `--ff-only`와 동일합니다.
  * `merge_opts::MergeOptions=MergeOptions()`: `merge_opts`는 충돌 발생 시 병합 전략과 같은 병합 옵션을 지정합니다.
  * `checkout_opts::CheckoutOptions=CheckoutOptions()`: `checkout_opts`는 체크아웃 단계에 대한 옵션을 지정합니다.

`git merge [--ff-only] [<committish> | <branch>]`와 동등합니다.

!!! note
    `branch`를 지정하는 경우, 이는 참조 형식으로 해야 합니다. 문자열이 `GitReference`로 변환되기 때문입니다. 예를 들어, 브랜치 `branch_a`를 병합하려면 `merge!(repo, branch="refs/heads/branch_a")`를 호출해야 합니다.

