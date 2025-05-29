```
Scale{S <: Union{Number, Val}, D, BT <: AbstractBlock{D}} <: TagBlock{BT, D}
Scale(factor, block)
```

Multiply a block with a scalar factor, which can be a number or a `Val`. If the factor is a number, it is regarded as a parameter that can be changed dynamically. If the factor is a `Val`, it is regarded as a constant.

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> 2 * X
[scale: 2] X

julia> im * Z
[+im] Z

julia> -im * Z
[-im] Z

julia> -Z
[-] Z
```
