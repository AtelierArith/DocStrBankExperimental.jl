```
replicated_crystal = replicate(crystal, repfactors)
```

`Crystal`内の原子と電荷を正の方向に複製して新しい`Crystal`を構築します。`replicate(crystal, (1, 1, 1))`は同じ`Crystal`を返すことに注意してください。分数座標は[0, 1]の範囲に再スケーリングされます。

# 引数

  * `crystal::Crystal`: 複製する結晶
  * `repfactors::Tuple{Int, Int, Int}`: 各結晶学的方向（a, b, c）で結晶構造を複製するための因子。

# 戻り値

  * `replicated_frame::Crystal`: 複製された結晶
