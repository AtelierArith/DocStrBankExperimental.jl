```
atan(y)
atan(y, x)
```

计算 `y` 或 `y/x` 的反正切。

对于一个实数参数，这是正 *x* 轴与点 (1, *y*) 之间的弧度角，返回值在区间 $[-\pi/2, \pi/2]$ 内。

对于两个参数，这是正 *x* 轴与点 (*x*, *y*) 之间的弧度角，返回值在区间 $[-\pi, \pi]$ 内。这对应于标准的 [`atan2`](https://en.wikipedia.org/wiki/Atan2) 函数。请注意，按照约定，当 `x < 0` 时，`atan(0.0,x)` 被定义为 $\pi$，而 `atan(-0.0,x)` 被定义为 $-\pi$。

另见 [`atand`](@ref) 以获取度数。

# 示例

```jldoctest
julia> rad2deg(atan(-1/√3))
-30.000000000000004

julia> rad2deg(atan(-1, √3))
-30.000000000000004

julia> rad2deg(atan(1, -√3))
150.0
```
