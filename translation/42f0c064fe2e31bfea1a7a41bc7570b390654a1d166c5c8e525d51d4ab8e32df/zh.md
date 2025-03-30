```
rot!(n, X, incx, Y, incy, c, s)
```

用 `c*X + s*Y` 覆盖 `X`，并用 `-conj(s)*X + c*Y` 覆盖 `Y`，针对数组 `X` 的前 `n` 个元素，步长为 `incx`，以及数组 `Y` 的前 `n` 个元素，步长为 `incy`。返回 `X` 和 `Y`。

!!! compat "Julia 1.5"
    `rot!` 至少需要 Julia 1.5。

