```
measure!([postprocess,] [operator, ]register[, locs]; rng=Random.GLOBAL_RNG)
```

現在アクティブなクディットまたは `locs` にあるクディットを測定します。オペレーターが提供されていない場合、計算基底で測定し、積状態に崩壊します。そうでない場合、量子状態は観測可能量の結果の固有値に対応する部分空間に崩壊します。

### 引数

  * `postprocess` は後処理メソッドで、次のように指定できます。

      * `NoPostProcess()`（デフォルト）。
      * `ResetTo(config)`、結果の状態を `config` にリセットします。オペレーターが提供されている場合には使用できません。なぜなら、一般にオペレーターを測定することは積状態を返さないからです。
      * `RemoveMeasured()`、測定されたクディットをレジスタから削除します。これも `operator` 引数とは互換性がありません。
  * `operator::AbstractBlock` は測定するオペレーターです。
  * `register::AbstractRegister` は量子状態です。
  * `locs` は測定を行うキュービットです。`locs` が提供されていない場合、すべての現在アクティブなクディットが測定されます（アクティブなクディットについては、

[`focus!`](@ref) および [`relax!`](@ref) を参照してください）。

### キーワード引数

  * `rng` は乱数生成器です。

### 例

次の例では、計算基底でランダム状態を測定し、特定のビット列値にリセットします。

```jldoctest; setup=:(using Yao, Random; Random.seed!(2))
julia> reg = rand_state(3);

julia> measure!(ResetTo(bit"011"), reg)
110 ₍₂₎

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 011 ₍₂₎
 011 ₍₂₎
 011 ₍₂₎

julia> measure!(RemoveMeasured(), reg, (1,2))
11 ₍₂₎

julia> reg  # 削除されたキュービットはもはや使用できません
ArrayReg{2, ComplexF64, Array...}
    active qubits: 1/1
    nlevel: 2
```

オペレーターを測定すると、状態は返された固有値に関連付けられた部分空間に投影されます。

```jldoctest; setup=:(using Yao, Random; Random.seed!(2))
julia> reg = uniform_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> print_table(reg)
000 ₍₂₎   0.35355 + 0.0im
001 ₍₂₎   0.35355 + 0.0im
010 ₍₂₎   0.35355 + 0.0im
011 ₍₂₎   0.35355 + 0.0im
100 ₍₂₎   0.35355 + 0.0im
101 ₍₂₎   0.35355 + 0.0im
110 ₍₂₎   0.35355 + 0.0im
111 ₍₂₎   0.35355 + 0.0im

julia> measure!(repeat(3, Z, 1:3), reg)
-1.0 + 0.0im

julia> print_table(reg)
000 ₍₂₎   0.0 + 0.0im
001 ₍₂₎   0.5 + 0.0im
010 ₍₂₎   0.5 + 0.0im
011 ₍₂₎   0.0 + 0.0im
100 ₍₂₎   0.5 + 0.0im
101 ₍₂₎   0.0 + 0.0im
110 ₍₂₎   0.0 + 0.0im
111 ₍₂₎   0.5 + 0.0im
```

ここでは、パリティオペレーターを測定しました。その結果、得られた状態は偶数または奇数のパリティを持つ部分空間に崩壊しました。
