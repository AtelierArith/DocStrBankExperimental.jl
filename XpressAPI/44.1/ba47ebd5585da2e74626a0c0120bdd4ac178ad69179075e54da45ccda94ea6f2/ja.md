```
XPRSloadmiqcqp64(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub, nobjqcoefs, objqcol1, objqcol2, objqcoef, nqrows, qrowind, nrowqcoefs, rowqcol1, rowqcol2, rowqcoef, nentities, nsets, coltype, entind, limit, settype, setstart, setind, refval)::prob
```

混合整数二次問題を最適化データ構造に読み込むために使用されます。

このような問題は、目的関数および制約に二次項を含むことがあります。整数、バイナリ、部分整数、半連続および半連続整数変数を定義でき、タイプ1および2のセットとともに使用できます。セットメンバーの参照行値は、参照行を指定するのではなく、配列として渡されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題の名前を含む最大MAXPROBNAMELENGTH文字の文字列。
  * `ncols::Integer`: 行列の構造列の数。
  * `nrows::Integer`: 行列の行数（目的行を含まない）。
  * `rowtype::AbstractVector{Cchar}`: 行タイプを含む長さ`nrows`の文字配列: Lは`<=`制約を示します（この制約は二次制約にも使用します）；Eは`=`制約を示します；Gは`>=`制約を示します；Rは範囲制約を示します；Nは非拘束制約を示します。
  * `rhs::AbstractVector{Number}`: 行の右辺係数を含む長さ`nrows`の倍精度配列。
  * `rng::AbstractVector{Number}`: 範囲行の範囲値を含む長さ`nrows`の倍精度配列。
  * `objcoef::AbstractVector{Number}`: 目的関数係数を含む長さ`ncols`の倍精度配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置を示す`rowind`および`rowcoef`配列のオフセットを含む整数配列。
  * `collen::AbstractVector{Integer}`: 各列の非ゼロ要素の数を含む長さ`ncols`の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の非ゼロ要素の行インデックスを含む整数配列。
  * `rowcoef::AbstractVector{Number}`: 非ゼロ要素の値を含む倍精度配列；`rowind`と同じ長さ。
  * `lb::AbstractVector{Number}`: 列の下限を含む長さ`ncols`の倍精度配列。
  * `ub::AbstractVector{Number}`: 列の上限を含む長さ`ncols`の倍精度配列。
  * `nobjqcoefs::Integer`: 二次項の数。
  * `objqcol1::AbstractVector{Integer}`: 各二次項の最初の変数の列インデックスを含む長さ`nobjqcoefs`の整数配列。
  * `objqcol2::AbstractVector{Integer}`: 各二次項の2番目の変数の列インデックスを含む長さ`nobjqcoefs`の整数配列。
  * `objqcoef::AbstractVector{Number}`: 二次係数を含む長さ`nobjqcoefs`の倍精度配列。
  * `nqrows::Integer`: 二次行列を含む行の数。
  * `qrowind::AbstractVector{Integer}`: 二次行列を含む行のインデックスを含む長さ`nqrows`の整数配列。
  * `nrowqcoefs::AbstractVector{Integer}`: 各二次制約行列の非ゼロの数を含む長さ`nqrows`の整数配列。
  * `rowqcol1::AbstractVector{Integer}`: `nqcelem`のサイズの整数配列で、`nqcelem`は`nrowqcoefs`の要素の合計（すなわち、すべての制約における二次行列要素の総数）に等しい。
  * `rowqcol2::AbstractVector{Integer}`: 二次制約行列の2番目のインデックスを含む長さ`nqcelem`の整数配列。
  * `rowqcoef::AbstractVector{Number}`: 二次制約行列の係数を含む長さ`nqcelem`の倍精度配列。
  * `nentities::Integer`: バイナリ、整数、半連続、半連続整数および部分整数エンティティの数。
  * `nsets::Integer`: SOS1およびSOS2セットの数。
  * `coltype::AbstractVector{Cchar}`: エンティティタイプを含む長さ`nentities`の文字配列: Bはバイナリ変数；Iは整数変数；Pは部分整数変数；Sは半連続変数；Rは半連続整数変数。
  * `entind::AbstractVector{Integer}`: MIPエンティティの列インデックスを含む長さ`nentities`の整数配列。
  * `limit::AbstractVector{Number}`: 部分整数変数の整数制限および半連続および半連続整数変数の下限を含む長さ`nentities`の倍精度配列（バイナリおよび整数変数に対応する位置のエントリは無視されます）。
  * `settype::AbstractVector{Cchar}`: セットタイプを含む長さ`nsets`の文字配列: 1はSOS1タイプセット；2はSOS2タイプセット。必要ない場合は`nothing`である可能性があります。
  * `setstart::AbstractVector{Integer}`: セットの開始を示す`setind`および`refval`配列のオフセットを含む整数配列。
  * `setind::AbstractVector{Integer}`: 各セットの列を含む長さ`setstart[nsets]-1`の整数配列。
  * `refval::AbstractVector{Number}`: 各セットメンバーの参照行エントリを含む長さ`setstart[nsets]-1`の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadmiqcqp64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmiqcqp64.html)のドキュメントも参照してください。
