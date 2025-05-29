```
control(n, ctrl_locs, locations => subblock)
```

`n`量子ビットの [`ControlBlock`](@ref) を返します。制御位置 `ctrl_locs` と第3引数のサブブロック `locations` は整数、タプル、または範囲であり、サブブロックのサイズは `locations` の長さと一致する必要があります。$I$ を $2 \times 2$ 単位行列、$G$ を $2 \times 2$ サブブロック、$P_0=|0\rangle\langle 0|$ および $P_1=|1\rangle\langle 1|$ をサブスペース $|0\rangle$ と $|1\rangle$ への2つの単一量子ビット射影演算子、$i$ と $j$ を $i>j$ となる2つの整数とします。`control(n, i, j=>G)` の行列表現は次のようになります。

$$
\begin{align}
&I^{\otimes n-i} P_0 \otimes I^{\otimes i-j-1} \otimes I\otimes I^{\otimes j-1}
+\\
& I^{\otimes n-i} P_1 \otimes I^{\otimes i-j-1} \otimes G\otimes I^{\otimes j-1}
\end{align}
$$

多重制御された多量子ビット制御ブロックはより複雑で、制御量子ビットがすべて1のときにゲートを適用することを意味します。各制御位置は逆制御を表すために負の符号を取ることができ、これはこの量子ビットが `0` のときのみ制御ゲートが適用されることを意味します。

### 例

```jldoctest; setup=:(using Yao)
julia> control(4, (1, 2), 3=>X)
nqubits: 4
control(1, 2)
└─ (3,) X

julia> control(4, 1, 3=>X)
nqubits: 4
control(1)
└─ (3,) X
```
