```
EntryTable{IT<:DitStr, ET}
```

ディット文字列振幅のテーブルで、例えばインデクシングや演算子の表現、または演算子インデクシングの出力を表すために使用できます。

### 例

```jldoctest; setup=:(using Yao)
julia> EntryTable([dit"121;3", dit"111;3"], [0.6, 0.8im])
EntryTable{DitStr64{3, 3}, ComplexF64}:
  121 ₍₃₎   0.6 + 0.0im
  111 ₍₃₎   0.0 + 0.8im
```

次の例では、ハミルトニアンを作成し、このハミルトニアンによってビット文字列を散乱させる方法を示します。

```jldoctest; setup=:(using Yao)
julia> b = kron(X,Z,Y)
nqubits: 3
kron
├─ 1=>X
├─ 2=>Z
└─ 3=>Y

julia> b[:,bit"010"]
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  111 ₍₂₎   0.0 - 1.0im

julia> b[:,b[:,bit"010"]]
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  010 ₍₂₎   1.0 + 0.0im
```
