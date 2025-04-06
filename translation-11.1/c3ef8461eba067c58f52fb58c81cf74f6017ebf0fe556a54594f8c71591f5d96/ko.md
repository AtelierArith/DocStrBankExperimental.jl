```
fetch(repo::GitRepo; kwargs...)
```

저장소 `repo`의 업스트림에서 업데이트를 가져옵니다.

키워드 인자는 다음과 같습니다:

  * `remote::AbstractString="origin"`: 가져올 `repo`의 원격 이름입니다. 비어 있으면 URL을 사용하여 익명 원격을 구성합니다.
  * `remoteurl::AbstractString=""`: `remote`의 URL입니다. 지정되지 않으면 주어진 `remote` 이름을 기반으로 가정됩니다.
  * `refspecs=AbstractString[]`: 가져오기 속성을 결정합니다.
  * `credentials=nothing`: 개인 `remote`에 대해 인증할 때 자격 증명 및/또는 설정을 제공합니다.
  * `callbacks=Callbacks()`: 사용자가 제공한 콜백 및 페이로드입니다.

`git fetch [<remoteurl>|<repo>] [<refspecs>]`와 동등합니다.
