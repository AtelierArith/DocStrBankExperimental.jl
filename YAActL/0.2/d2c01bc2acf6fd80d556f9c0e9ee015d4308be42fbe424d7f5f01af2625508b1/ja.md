```
exec!(lk::Link, from::Link, f::Function, args...; kwargs...)
exec!(lk::Link, from::Link, fu::Func)
exec!(lk::Link, fu::Func; timeout::Real=5.0)
exec!(name::Symbol, ....)
```

アクター `lk`（または登録されている場合は `name`）に任意の関数を実行させ、その返された値を [`Response`](@ref) として送信します。

# 引数

  * アクターの `lk::Link` または `name::Symbol`、
  * `from::Link`: `Response` を送信するリンク。 `from` が省略された場合、`exec!` はブロックし、待機して結果を返します。その場合、タイムアウトがあります。
  * `f::Function, args...; kwargs...` または
  * `fu::Func`: 関数の引数、
  * `timeout::Real=5.0`: タイムアウト（秒）。タイムアウトを望まない場合は `timeout=Inf` に設定します。
