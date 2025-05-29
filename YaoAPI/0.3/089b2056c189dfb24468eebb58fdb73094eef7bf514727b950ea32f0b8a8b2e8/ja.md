```
fidelity(register1, register2)
```

2つの状態間の忠実度を返します。

# 定義

量子状態の忠実度は、quditsの場合次のように定義されます：

$$
F(ρ, σ) = tr(\sqrt{\sqrt{ρ}σ\sqrt{ρ}})
$$

または、数値計算で使用する同等の形式：

$$
F(ρ, σ) = sqrt(tr(ρσ) + 2 \sqrt{det(ρ)det(σ)})
$$

# 参考文献

  * Jozsa R. 混合量子状態の忠実度[J]. Journal of modern optics, 1994, 41(12): 2315-2323.
  * Nielsen M A, Chuang I. 量子計算と量子情報[J]. 2002.

!!! 注     忠実度 $F$ の元の定義は、1994年にJozsaによって定義された「遷移確率」からのもので、ここで使用するものの平方です。
