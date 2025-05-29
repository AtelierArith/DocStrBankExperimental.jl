```
query!(lk::Link, from::Link, s::Symbol)
query!(lk::Link, s::Symbol; timeout::Real=5.0)
query!(name::Symbol, ....)
```

`lk` アクターに、内部状態変数 `s` を持つ [`Response`](@ref) メッセージを `from` に送信するように依頼します。

`from` が省略されると、`query!` はブロックし、応答を返します。その場合、`timeout` があります。

  * `s::Symbol` は `:sta`, `:res`, `:bhv`, `:dsp` のいずれかです。

# 例

```julia
julia> f(x, y; u=0, v=0) = x+y+u+v  # 挙動を実装する
f (generic function with 1 method)

julia> fact = Actor(f, 1)     # それを使ってアクターを開始する
Channel{Message}(sz_max:32,sz_curr:0)

julia> cast!(fact, 1)         # それに第二のパラメータをキャストする
YAActL.Cast{Tuple{Int64}}((1,))

julia> query!(fact, :res)     # 結果を問い合わせる
2

julia> query!(fact, :bhv)     # 挙動を問い合わせる
f (generic function with 1 method)

julia> set!(fact, state)      # ディスパッチモードを設定する
YAActL.Update{Dispatch}(:dsp, state)

julia> query!(fact, :dsp)     # ディスパッチモードを問い合わせる
state::Dispatch = 1

julia> update!(fact, 10)      # 状態を更新する
YAActL.Update{Int64}(:sta, 10)

julia> query!(fact)           # 状態変数を問い合わせる
10

julia> call!(fact, 1)
11
```
