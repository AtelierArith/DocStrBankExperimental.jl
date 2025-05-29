```
measure!([postprocess,] [operator, ]register[, locs]; rng=Random.GLOBAL_RNG)
```

現在アクティブなクディットまたは `locs` のクディットを測定します。測定と崩壊の後、

```
* postprocess が `NoPostProcess` の場合は何もしない
* postprocess が `ResetTo` の場合は結果の状態を `postprocess.config` にリセットする
* postprocess が `RemoveMeasured` の場合はキュービットを削除する
```
