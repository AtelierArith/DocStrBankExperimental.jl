```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

주어진 진수에서 `n`의 자릿수를 가진 요소 유형 `T`(기본값 `Int`)의 배열을 반환하며, 선택적으로 지정된 크기로 0으로 패딩할 수 있습니다. 더 중요한 자릿수는 더 높은 인덱스에 위치하며, 따라서 `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))`입니다.

또한 [`ndigits`](@ref), [`digits!`](@ref), 그리고 진수 2의 경우 [`bitstring`](@ref), [`count_ones`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> digits(10)
2-element Vector{Int64}:
 0
 1

julia> digits(10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits(-256, base = 10, pad = 5)
5-element Vector{Int64}:
 -6
 -5
 -2
  0
  0

julia> n = rand(-999:999);

julia> n == evalpoly(13, digits(n, base = 13))
true
```
