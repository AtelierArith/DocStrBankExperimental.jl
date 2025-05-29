```
become!(lk::Link, bhv::Function, args1...; kwargs...)
become!(name::Symbol, ....)
```

アクターの振る舞いを変更します。

# 引数

  * アクター `lk::Link`（または登録されている場合は `name::Symbol`）,
  * `bhv`: 新しい振る舞いを実装する関数,
  * `args1...`: `bhv` への最初の引数（可能な `msg` 引数なし）,
  * `kwargs...`: `bhv` へのキーワード引数.
