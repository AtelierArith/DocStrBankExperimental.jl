```
wrap!(f::Frac)
wrap!(crystal::Crystal)
```

分数座標を `mod(⋅, 1.0)` を介して [0, 1] にラップします。例えば、-0.1 –> 0.9 および 1.1 -> 0.1
