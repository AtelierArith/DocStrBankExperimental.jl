```
hardlink(src::AbstractString, dst::AbstractString)
```

기존 소스 파일 `src`에 대한 하드 링크를 이름 `dst`로 생성합니다. 목적지 `dst`는 존재하지 않아야 합니다.

또한: [`symlink`](@ref).

!!! compat "Julia 1.8"
    이 메서드는 Julia 1.8에 추가되었습니다.

