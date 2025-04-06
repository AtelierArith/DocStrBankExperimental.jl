```
iswritable(io) -> Bool
```

지정된 IO 객체가 쓸 수 없는 경우 `false`를 반환합니다.

# 예제

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           iswritable(io)
       end
true

julia> open("myfile.txt", "r") do io
           iswritable(io)
       end
false

julia> rm("myfile.txt")
```
