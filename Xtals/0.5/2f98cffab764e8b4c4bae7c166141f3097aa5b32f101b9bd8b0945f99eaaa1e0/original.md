```
wrap!(f::Frac)
wrap!(crystal::Crystal)
```

wrap fractional coordinates to [0, 1] via `mod(⋅, 1.0)`. e.g. -0.1 –> 0.9 and 1.1 -> 0.1
