```
fidelity(register1, register2) -> Real/Vector{<:Real}
fidelity'(pair_or_reg1, pair_or_reg2) -> (g1, g2)
```

2つの状態間のフィデリティを返します。`r1`と`r2`の間のフィデリティを計算します。もし`r1`または`r2`が純粋状態でない場合（`nactive(r) != nqudits(r)`）、フィデリティは浄化によって計算されます。詳細は、http://iopscience.iop.org/article/10.1088/1367-2630/aa6a4b/metaを参照してください。

レジスタと回路パラメータに関する勾配を取得します。ペア入力`ψ=>circuit`の場合、返される勾配は`gψ=>gparams`のペアであり、`gψ`は入力状態の勾配、`gparams`は回路パラメータの勾配です。レジスタ入力の場合、返される値はレジスタです。

### 定義

2つの量子状態のフィデリティは、次のように定義されます：

$$
F(ρ, σ) = tr(\sqrt{\sqrt{ρ}σ\sqrt{ρ}})
$$

!!! note
    この定義は、[Wikiの定義](https://en.wikipedia.org/wiki/Fidelity_of_quantum_states)とは異なり、平方が含まれています。


### 例

```jldoctest; setup=:(using Yao)
julia> reg1 = uniform_state(3);

julia> reg2 = zero_state(3);

julia> fidelity(reg1, reg2)
0.35355339059327373
```

### 参考文献

  * Jozsa R. 混合量子状態のフィデリティ[J]. Journal of modern optics, 1994, 41(12): 2315-2323.
  * Nielsen M A, Chuang I. 量子計算と量子情報[J]. 2002.

!!! note
    フィデリティ$F$の元の定義は「遷移確率」から来ており、1994年にJozsaによって定義されました。これは、ここで使用するものの平方です。

