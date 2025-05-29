```
print_block(io, block)
```

Define how blocks are printed as text in one line.

### Examples

```jldoctest; setup=:(using Yao)
julia> print_block(stdout, X)
X

julia> print_block(stdout, put(2, 1=>X))
put on (1)
```
