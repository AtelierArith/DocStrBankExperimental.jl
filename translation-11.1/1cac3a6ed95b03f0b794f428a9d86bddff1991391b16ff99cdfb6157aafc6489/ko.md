```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

주어진 url에서 파일을 다운로드하여 `path` 위치에 저장합니다. 지정하지 않으면 임시 경로에 저장됩니다. 다운로드된 파일의 경로를 반환합니다.

!!! note
    Julia 1.6부터 이 함수는 더 이상 사용되지 않으며 `Downloads.download`에 대한 얇은 래퍼일 뿐입니다. 새로운 코드에서는 이 함수를 호출하는 대신 해당 함수를 직접 사용해야 합니다.

