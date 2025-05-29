```
time_evolve(H, dt[; tol=1e-7, check_hermicity=true])
```

[`TimeEvolution`](@ref) ブロックをハミルトニアン `H` と時間ステップ `dt` で作成します。`TimeEvolution` ブロックは、Krylove ベースの `expv` を使用して時間伝播を計算します。`TimeEvolution` ブロックは、`dt` が複素数の場合に [虚時間進化](http://large.stanford.edu/courses/2008/ph372/behroozi2/) にも使用できます。$H$ をハミルトニアン、$t$ を時間とすると、`time_evolve(H, t)` の行列表現は $e^{-iHt}$ です。

### 引数

  * `H` は `AbstractBlock` として表現されたハミルトニアンです。
  * `dt`: 進化の期間（開始時間はゼロです）。

### キーワード引数

  * `tol::Real=1e-7`: 誤差許容値。
  * `check_hermicity=true`: エルミート性をチェックするかどうか。

### 例

```jldoctest; setup=:(using Yao)
julia> time_evolve(kron(2, 1=>X, 2=>X), 0.1)
Time Evolution Δt = 0.1, tol = 1.0e-7
kron
├─ 1=>X
└─ 2=>X
```
