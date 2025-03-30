```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

重新设置随机数生成器：`rng` 只有在提供 `seed` 时才会生成可重复的数字序列。一些 RNG 不接受种子，例如 `RandomDevice`。在调用 `seed!` 之后，`rng` 等价于一个使用相同种子初始化的新创建对象。接受的种类的种子取决于 `rng` 的类型，但一般来说，整数种子应该有效。

如果未指定 `rng`，则默认对共享的任务本地生成器的状态进行种子设置。

# 示例

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # 不可重复
true

julia> rand(Random.seed!(rng), Bool) # 也不可重复
false

julia> rand(Xoshiro(), Bool) # 也不可重复
true
```
