制御ブロックは、制御キュービットがすべて1のときにブロックを適用する合成ブロックです。

!!! note
    制御キュービットのインデックスが負の場合、それは逆制御を意味します。つまり、制御キュービットがゼロのときにブロックが適用されます。


### フィールド

  * `n::Int64`
  * `ctrl_locs::NTuple{C, Int64} where C`
  * `ctrl_config::NTuple{C, Int64} where C`
  * `content::YaoAPI.AbstractBlock`
  * `locs::NTuple{M, Int64} where M`
