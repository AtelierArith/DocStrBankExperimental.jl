```
neutral(charges, tol) # true または false。デフォルト tol = 1e-5
neutral(crystal, tol) # true または false。デフォルト tol = 1e-5
```

`charges::Charges` のセット (`charges.q`) が `tol::Float64` より小さい絶対値の合計であるかどうかを判断します。`crystal::Crystal` が渡された場合、関数は `crystal.charges` を見ます。すなわち、ネットチャージの絶対値が `tol` より小さいかどうかを判断します。
