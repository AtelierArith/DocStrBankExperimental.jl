```
pullback(f, args...)
pullback(f, ::Params)
```

関数 `f` の値と、各引数 `x` に対する `∂f/∂x` を含むタプルを取得するために呼び出すことができるバックプロパゲータ関数を返します。これはスカラー `x` の場合は導関数、その他の場合は勾配です。

```julia
y, back = pullback(f, args...)
∇ = back(seed)
```

`back` は `f(args...)` の出力に一致する開始値 `seed` で呼び出す必要があります。もし `f(args...)` が数値を返す場合、`seed` も数値であるべきです。もし `f(args...)` が配列を返す場合、`seed` は同じサイズの配列であるべきです。

値と勾配を1回の呼び出しで取得するためには [`withgradient`](@ref) を、勾配のみを取得するためには [`gradient`](@ref) を参照してください。

```jldoctest; setup=:(using Zygote)
julia> y, back = pullback(*, 2.0, 3.0, 5.0);

julia> y
30.0

julia> back(1.0)
(15.0, 10.0, 6.0)

julia> back(2.0)
(30.0, 20.0, 12.0)

julia> y, back = pullback(x -> [x, x], 1.0);

julia> y
2-element Vector{Float64}:
 1.0
 1.0

julia> back([1.0, 1.0])
(2.0,)

julia> back([2.0, nothing])
(2.0,)
```
