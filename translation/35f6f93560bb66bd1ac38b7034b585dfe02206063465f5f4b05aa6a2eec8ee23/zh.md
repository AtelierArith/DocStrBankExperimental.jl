```
evalpoly(x, p)
```

评估多项式 $\sum_k x^{k-1} p[k]$，其中系数为 `p[1]`、`p[2]` 等；也就是说，系数按 `x` 的幂的升序给出。如果系数的数量是静态已知的，即当 `p` 是一个 `Tuple` 时，循环将在编译时展开。该函数使用霍纳法则生成高效代码，如果 `x` 是实数，或者使用类似 Goertzel 的 [^DK62] 算法，如果 `x` 是复数。

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    此函数需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
