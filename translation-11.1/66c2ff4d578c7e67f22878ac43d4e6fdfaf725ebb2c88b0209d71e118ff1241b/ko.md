```
dump(x; maxdepth=8)
```

값의 표현의 모든 부분을 보여줍니다. 출력의 깊이는 `maxdepth`에서 잘립니다.

# 예제

```jldoctest
julia> struct MyStruct
           x
           y
       end

julia> x = MyStruct(1, (2,3));

julia> dump(x)
MyStruct
  x: Int64 1
  y: Tuple{Int64, Int64}
    1: Int64 2
    2: Int64 3

julia> dump(x; maxdepth = 1)
MyStruct
  x: Int64 1
  y: Tuple{Int64, Int64}
```
