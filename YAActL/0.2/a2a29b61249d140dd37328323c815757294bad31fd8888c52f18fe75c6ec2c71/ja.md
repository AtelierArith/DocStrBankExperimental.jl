```
init!(lk::Link, f::Function, args...; kwargs...)
init!(name::Symbol, ....)
```

アクター `lk` に、与えられた引数を持つ関数 `f` を [`init`](@ref _ACT) 関数として保存し、それを実行し、返された値を状態 [`sta`](@ref _ACT) 変数として保存するように指示します。

`init` 関数はアクターの再起動時に呼び出されます。

!!! note "この動作はまだ実装されていません！"
    監視のために必要です。

