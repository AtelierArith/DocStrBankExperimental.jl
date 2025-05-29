```
new_box = replicate(original_box, repfactors)
```

正の方向に `Box` を複製して、新しい `Box` を構築し、スーパーセルを表します。`original_box` は `repfactors` の因子に従って複製されます。`replicate(original_box, repfactors=(1, 1, 1))` は同じ `Box` を返すことに注意してください。`f_to_c` と `c_to_f` によって記述される新しい分数座標は依然として ∈ [0, 1] です。

# 引数

  * `original_box::Box`: 複製したいボックス
  * `repfactors::Tuple{Int, Int, Int}`: ボックスを複製するための因子

# 戻り値

  * `box::Box`: 完全に形成された Box オブジェクト
