```
convert(T, x)
```

`x`를 타입 `T`의 값으로 변환합니다.

`T`가 [`Integer`](@ref) 타입인 경우, `x`가 `T`로 표현할 수 없는 경우에는 [`InexactError`](@ref)가 발생합니다. 예를 들어, `x`가 정수 값이 아니거나 `T`가 지원하는 범위를 벗어나는 경우입니다.

# 예제

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
ERROR: InexactError: Int64(3.5)
Stacktrace:
[...]
```

`T`가 [`AbstractFloat`](@ref) 타입인 경우, `T`로 표현할 수 있는 `x`에 가장 가까운 값을 반환합니다. Inf는 가장 가까운 값을 결정하는 데 있어 `floatmax(T)`보다 하나 더 큰 ulp로 처리됩니다.

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

`T`가 컬렉션 타입이고 `x`가 컬렉션인 경우, `convert(T, x)`의 결과는 `x`의 전체 또는 일부를 별칭할 수 있습니다.

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

또한 참조: [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref).
