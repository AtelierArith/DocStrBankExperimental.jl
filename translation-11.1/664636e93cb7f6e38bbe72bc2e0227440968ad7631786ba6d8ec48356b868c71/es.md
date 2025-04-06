```
transpose(A)
```

Transposición perezosa. Mutar el objeto devuelto debería mutar apropiadamente `A`. A menudo, pero no siempre, produce `Transpose(A)`, donde `Transpose` es un envoltorio de transposición perezosa. Tenga en cuenta que esta operación es recursiva.

Esta operación está destinada al uso en álgebra lineal; para manipulación de datos general, consulte [`permutedims`](@ref Base.permutedims), que no es recursiva.

# Ejemplos

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # la transposición de una transposición desenvuelve el padre
true

julia> Transpose(B) # sin embargo, el constructor siempre envuelve su argumento
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # modificar B modificará A automáticamente

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

Para matrices complejas, la operación `adjoint` es equivalente a una transposición conjugada.

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

La `transpose` de un `AbstractVector` es un vector fila:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # devuelve un vector fila
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # calcular el producto punto
14
```

Para una matriz de matrices, los bloques individuales se operan recursivamente:

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # construir una matriz de bloques
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # los bloques se transponen recursivamente
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
