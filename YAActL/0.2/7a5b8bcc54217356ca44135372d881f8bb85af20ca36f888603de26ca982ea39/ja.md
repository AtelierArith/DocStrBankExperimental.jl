```
update!(lk::Link, x; s::Symbol=:sta)
update!(lk::Link, arg::Args)
update!(name::Symbol, ....)
```

アクターの内部状態`s`を`args...`で更新します。

# 引数

  * アクター`lk::Link`または`name::Symbol`（登録されている場合）、
  * `x`: 選択した状態を更新するための値/変数、
  * `arg::Args`: 更新するための引数、
  * `s::Symbol`: `:sta`、`:dsp`、`:arg`、`:self`、`:name`のいずれか。

*注:* `s=:arg`で動作関数に保存された引数を更新したい場合は、`arg`に[`Args`](@ref)を渡す必要があります。`Args`にキーワード引数がある場合、それらは動作関数の既存のキーワード引数とマージされます。

# 例

```julia
julia> update!(fact, 5)       # factが状態dispatchにあることに注意
YAActL.Update{Int64}(:sta, 5)

julia> call!(fact, 5)         # 5で呼び出す
10

julia> update!(fact, Args(0, u=5));  # 引数を更新

julia> call!(fact, 5)         # 最後の結果、5とu=5を加える
20
```
