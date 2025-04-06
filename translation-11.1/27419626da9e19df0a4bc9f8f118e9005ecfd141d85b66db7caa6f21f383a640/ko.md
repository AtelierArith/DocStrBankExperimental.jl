```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

파일, 링크 또는 디렉토리를 `src`에서 `dst`로 복사합니다. `force=true`이면 기존의 `dst`를 먼저 제거합니다.

`follow_symlinks=false`이고 `src`가 심볼릭 링크인 경우, `dst`는 심볼릭 링크로 생성됩니다. `follow_symlinks=true`이고 `src`가 심볼릭 링크인 경우, `dst`는 `src`가 참조하는 파일 또는 디렉토리의 복사가 됩니다. `dst`를 반환합니다.

!!! note
    `cp` 함수는 `cp` 명령과 다릅니다. `cp` 함수는 항상 `dst`가 파일이라는 가정 하에 작동하는 반면, 명령은 `dst`가 디렉토리인지 파일인지에 따라 다른 작업을 수행합니다. `dst`가 디렉토리일 때 `force=true`를 사용하면 `dst` 디렉토리에 있는 모든 내용이 손실되며, `dst`는 대신 `src`의 내용을 가진 파일이 됩니다.

