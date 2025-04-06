```
reverseind(v, i)
```

주어진 인덱스 `i`에 대해 [`reverse(v)`](@ref)에서 `v`의 해당 인덱스를 반환하여 `v[reverseind(v,i)] == reverse(v)[i]`가 성립하도록 합니다. (이는 `v`에 비ASCII 문자가 포함된 경우 비트리비얼할 수 있습니다.)

# 예제

```jldoctest
julia> s = "Julia🚀"
"Julia🚀"

julia> r = reverse(s)
"🚀ailuJ"

julia> for i in eachindex(s)
           print(r[reverseind(r, i)])
       end
Julia🚀
```
