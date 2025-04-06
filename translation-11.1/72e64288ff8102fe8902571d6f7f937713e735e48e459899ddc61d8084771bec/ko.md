```
for outer
```

`for` 루프에서 반복을 위해 기존의 지역 변수를 재사용합니다.

자세한 내용은 [변수 범위에 대한 매뉴얼 섹션](@ref scope-of-variables)을 참조하십시오.

또한 [`for`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # 비어 있음
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # 비어 있음
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # 전역 변수
       for outer i = 1:3
       end
ERROR: syntax: no outer local variable declaration exists for "for outer"
[...]
```
