```
Daggered(block)
```

[`Daggered`](@ref) ブロックを作成します。$G$ を入力ブロックとし、コード内の `G'` または `Daggered(block)` は $G^\dagger$ を表します。

### 例

逆QFTはエルミートではないため、`Daggered` ブロックでタグ付けされます。

```jldoctest; setup=:(using YaoBlocks)
julia> A(i, j) = control(i, j=>shift(2π/(1<<(i-j+1))));

julia> B(n, i) = chain(n, i==j ? put(i=>H) : A(j, i) for j in i:n);

julia> qft(n) = chain(B(n, i) for i in 1:n);

julia> struct QFT <: PrimitiveBlock{2} n::Int end

julia> YaoBlocks.nqudits(q::QFT) = q.n


julia> circuit(q::QFT) = qft(nqubits(q));

julia> YaoBlocks.mat(x::QFT) = mat(circuit(x));

julia> QFT(2)'
 [†]QFT
```
