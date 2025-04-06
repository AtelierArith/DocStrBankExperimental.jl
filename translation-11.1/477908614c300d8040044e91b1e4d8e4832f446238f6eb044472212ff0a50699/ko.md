```
isreadable(io) -> Bool
```

지정된 IO 객체가 읽을 수 없는 경우 `false`를 반환합니다.

# 예시

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           isreadable(io)
       end
false

julia> open("myfile.txt", "r") do io
           isreadable(io)
       end
true

julia> rm("myfile.txt")
```
