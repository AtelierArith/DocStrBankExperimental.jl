```
yao2einsum(circuit; initial_state=Dict(), final_state=Dict(), optimizer=TreeSA())
yao2einsum(circuit, initial_state::Dict, final_state::Dict, optimizer)
```

Yao `circuit` を一般化テンソルネットワーク（einsum）表記に変換します。返り値は [`TensorNetwork`](@ref) インスタンスです。

### 引数

  * `circuit` は入力としての Yao ブロックです。
  * `initial_state` と `final_state` は初期状態と最終状態を指定するための辞書です（共役を取る）。

      * 最初のインターフェースでは、状態は整数として指定されます。例えば、`Dict(1=>1, 2=>1, 3=>0, 4=>1)` は積状態 `|1⟩⊗|1⟩⊗|0⟩⊗|1⟩` を指定します。
      * 二番目のインターフェースでは、状態は `ArrayReg` として指定されます。例えば、`Dict(1=>rand_state(1), 2=>rand_state(1))`。

初期状態または最終状態で指定されていない量子ビットは、テンソルネットワーク内の自由な脚として扱われます。

  * `optimizer` はテンソルネットワークを最適化するために使用される最適化手法です。デフォルトは `TreeSA()` です。

詳細については [OMEinsumContractors.jl](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) をご覧ください。

```jldoctest
julia> using Yao

julia> c = chain(3, put(3, 2=>X), put(3, 1=>Y), control(3, 1, 3=>Y))
nqubits: 3
chain
├─ put on (2)
│  └─ X
├─ put on (1)
│  └─ Y
└─ control(1)
   └─ (3,) Y


julia> yao2einsum(c; initial_state=Dict(1=>0, 2=>1), final_state=Dict(1=>ArrayReg([0.6, 0.8im]), 2=>1))
TensorNetwork
Time complexity: 2^4.700439718141093
Space complexity: 2^2.0
Read-write complexity: 2^6.0
```
