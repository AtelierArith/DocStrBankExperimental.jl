```
push(repo::GitRepo; kwargs...)
```

`repo`의 업스트림에 업데이트를 푸시합니다.

키워드 인자는 다음과 같습니다:

  * `remote::AbstractString="origin"`: 푸시할 업스트림 원격의 이름입니다.
  * `remoteurl::AbstractString=""`: `remote`의 URL입니다.
  * `refspecs=AbstractString[]`: 푸시의 속성을 결정합니다.
  * `force::Bool=false`: 푸시가 강제 푸시인지, 즉 원격 브랜치를 덮어쓸지를 결정합니다.
  * `credentials=nothing`: 개인 `remote`에 대해 인증할 때 자격 증명 및/또는 설정을 제공합니다.
  * `callbacks=Callbacks()`: 사용자가 제공한 콜백 및 페이로드입니다.

`git push [<remoteurl>|<repo>] [<refspecs>]`와 동등합니다.
