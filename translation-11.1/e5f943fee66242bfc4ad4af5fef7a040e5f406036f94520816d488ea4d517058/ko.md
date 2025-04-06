```
abspath(path::AbstractString) -> String
```

현재 디렉토리를 추가하여 경로를 절대 경로로 변환합니다. 또한 [`normpath`](@ref)와 같이 경로를 정규화합니다.

# 예제

`JuliaExample`이라는 디렉토리에 있고 사용 중인 데이터가 `JuliaExample` 디렉토리에서 두 단계 위에 있는 경우 다음과 같이 작성할 수 있습니다:

```
abspath("../../data")
```

이것은 `"/home/JuliaUser/data/"`와 같은 경로를 제공합니다.

또한 [`joinpath`](@ref), [`pwd`](@ref), [`expanduser`](@ref)를 참조하세요.
