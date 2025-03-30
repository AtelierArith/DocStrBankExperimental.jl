```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

정수 파일 설명자에서 [`IOStream`](@ref) 객체를 생성합니다. `own`이 `true`인 경우, 이 객체를 닫으면 기본 설명자가 닫힙니다. 기본적으로 `IOStream`은 가비지 컬렉션될 때 닫힙니다. `name`을 사용하면 설명자를 이름이 있는 파일과 연결할 수 있습니다.
