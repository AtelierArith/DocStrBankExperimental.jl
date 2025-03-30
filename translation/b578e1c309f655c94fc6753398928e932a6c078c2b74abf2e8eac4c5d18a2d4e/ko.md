```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

지정된 `rmt` 원격 git 저장소에서 가져오고, `refspecs`를 사용하여 가져올 원격 브랜치를 결정합니다. 키워드 인자는 다음과 같습니다:

  * `options`: 가져오기 옵션을 결정합니다. 예를 들어, 이후에 가지치기를 할지 여부입니다. 더 많은 정보는 [`FetchOptions`](@ref)를 참조하세요.
  * `msg`: reflogs에 삽입할 메시지입니다.
