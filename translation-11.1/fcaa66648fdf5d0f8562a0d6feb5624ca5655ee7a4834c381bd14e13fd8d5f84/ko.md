```
open(f::Function, args...; kwargs...)
```

함수 `f`를 `open(args...; kwargs...)`의 결과에 적용하고 완료 후 결과 파일 디스크립터를 닫습니다.

# 예시

```jldoctest
julia> write("myfile.txt", "Hello world!");

julia> open(io->read(io, String), "myfile.txt")
"Hello world!"

julia> rm("myfile.txt")
```
