```
for outer
```

`for` ループで反復のために既存のローカル変数を再利用します。

詳細については、[変数のスコープに関するマニュアルセクション](@ref scope-of-variables)を参照してください。

また、[`for`](@ref)も参照してください。

# 例

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # 空
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # 空
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # グローバル変数
       for outer i = 1:3
       end
ERROR: 構文エラー: "for outer" に対する外部ローカル変数宣言が存在しません
[...]
```
