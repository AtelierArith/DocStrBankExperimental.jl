```
focus!(register, locs) -> register
focus!(locs...) -> f(register) -> register
```

アクティブな量子ビットをフォーカスされた位置に設定します。通常はサブルーチンを実行するために使用されます。`register`が提供されていない場合、レジスタを入力として受け取るラムダを返します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> focus!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/5
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 111 ₍₂₎
 111 ₍₂₎
 111 ₍₂₎

julia> measure(apply(reg, put(3, 2=>X)); nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 101 ₍₂₎
 101 ₍₂₎
 101 ₍₂₎
```

ここでは、プロダクト状態を準備し、量子ビット1、3、4のみに注目します。測定結果はすべて1です。フォーカスされたレジスタを使用すると、量子ビットの数が5であっても、サイズ3のブロックを適用できます。
