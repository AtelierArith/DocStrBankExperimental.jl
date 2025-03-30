```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

지정된 `rmt` 원격 git 저장소에 푸시하며, `refspecs`를 사용하여 푸시할 원격 브랜치를 결정합니다. 키워드 인자는 다음과 같습니다:

  * `force`: `true`인 경우, 충돌을 무시하고 강제 푸시가 발생합니다.
  * `options`: 푸시에 대한 옵션을 결정하며, 예를 들어 사용할 프록시 헤더를 설정합니다. 더 많은 정보는 [`PushOptions`](@ref)를 참조하세요.

!!! note
    푸시 refspecs에 대한 정보를 두 가지 다른 방법으로 추가할 수 있습니다: 저장소의 `GitConfig`에서 옵션을 설정하거나(`push.default`를 키로 사용) [`add_push!`](@ref)를 호출하는 것입니다. 그렇지 않으면 `push` 호출에서 푸시 refspec을 명시적으로 지정해야 효과가 있습니다. 예를 들어: `LibGit2.push(repo, refspecs=["refs/heads/master"])`.

