```
splitdir(path::AbstractString) -> (AbstractString, AbstractString)
```

경로를 디렉토리 이름과 파일 이름의 튜플로 분할합니다.

# 예시

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
