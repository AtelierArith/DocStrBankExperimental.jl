```
rotate!(x, y, c, s)
```

用 `c*x + s*y` 覆盖 `x`，用 `-conj(s)*x + c*y` 覆盖 `y`。返回 `x` 和 `y`。

!!! compat "Julia 1.5"
    `rotate!` 至少需要 Julia 1.5。

