```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

파일에 연결되지 않은 제로 초기화된 mmapped-memory를 생성하기 위한 `IO`-유사 객체를 생성합니다. [`mmap`](@ref mmap)에서 사용됩니다. `SharedArray`에서 공유 메모리 배열을 생성하는 데 사용됩니다.

# 예제

```jldoctest
julia> using Mmap

julia> anon = Mmap.Anonymous();

julia> isreadable(anon)
true

julia> iswritable(anon)
true

julia> isopen(anon)
true
```
