```
IdDict([itr])
```

`IdDict{K,V}()` は、[`objectid`](@ref) をハッシュとして、`===` を等価性として使用し、キーの型 `K` と値の型 `V` を持つハッシュテーブルを構築します。詳細については [`Dict`](@ref) を参照し、これのセットバージョンについては [`IdSet`](@ref) を参照してください。

以下の例では、`Dict` のキーはすべて `isequal` であり、したがって同じようにハッシュされ、上書きされます。`IdDict` はオブジェクトIDでハッシュされるため、3つの異なるキーを保持します。

# 例

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
