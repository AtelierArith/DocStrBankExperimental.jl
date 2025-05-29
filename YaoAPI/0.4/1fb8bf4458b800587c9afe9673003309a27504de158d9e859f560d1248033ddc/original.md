```
mat([T=ComplexF64], blk)
```

Returns the most compact matrix form of given block, e.g

### Examples

```jldoctest; setup=:(using Yao)
julia> mat(X)
2×2 LuxurySparse.SDPermMatrix{ComplexF64, Int64, Vector{ComplexF64}, Vector{Int64}}:
 0.0+0.0im  1.0+0.0im
 1.0+0.0im  0.0+0.0im

julia> mat(Float64, X)
2×2 LuxurySparse.SDPermMatrix{Float64, Int64, Vector{Float64}, Vector{Int64}}:
 0.0  1.0
 1.0  0.0

julia> mat(kron(X, X))
4×4 LuxurySparse.SDPermMatrix{ComplexF64, Int64, Vector{ComplexF64}, Vector{Int64}}:
 0.0+0.0im  0.0+0.0im  0.0+0.0im  1.0+0.0im
 0.0+0.0im  0.0+0.0im  1.0+0.0im  0.0+0.0im
 0.0+0.0im  1.0+0.0im  0.0+0.0im  0.0+0.0im
 1.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im

julia> mat(kron(X, X) + put(2, 1=>X))
4×4 SparseMatrixCSC{ComplexF64, Int64} with 8 stored entries:
     ⋅      1.0+0.0im      ⋅      1.0+0.0im
 1.0+0.0im      ⋅      1.0+0.0im      ⋅
     ⋅      1.0+0.0im      ⋅      1.0+0.0im
 1.0+0.0im      ⋅      1.0+0.0im      ⋅    
```
