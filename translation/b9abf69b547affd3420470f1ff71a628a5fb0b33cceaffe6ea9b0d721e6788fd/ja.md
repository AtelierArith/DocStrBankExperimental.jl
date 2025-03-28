```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

与えられた値にグローバルを取得し、条件付きで設定する操作を原子的に実行します。

!!! compat "Julia 1.11"
    この関数はJulia 1.11以降が必要です。


他に[`replaceproperty!`](@ref Base.replaceproperty!)および[`setglobal!`](@ref)を参照してください。
