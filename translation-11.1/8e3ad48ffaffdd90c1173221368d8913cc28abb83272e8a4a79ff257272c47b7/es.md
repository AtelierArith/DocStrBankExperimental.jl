```
similar(array, [element_type=eltype(array)], [dims=size(array)])
```

Crea un arreglo mutable no inicializado con el tipo de elemento y tamaño dados, basado en el arreglo fuente proporcionado. Los segundo y tercer argumentos son opcionales, y por defecto son el `eltype` y `size` del arreglo dado. Las dimensiones pueden especificarse ya sea como un solo argumento de tupla o como una serie de argumentos enteros.

Los subtipos de AbstractArray personalizados pueden elegir qué tipo de arreglo específico es el más adecuado para devolver según el tipo de elemento y la dimensionalidad dados. Si no especializan este método, el valor por defecto es un `Array{element_type}(undef, dims...)`.

Por ejemplo, `similar(1:10, 1, 4)` devuelve un `Array{Int,2}` no inicializado ya que los rangos no son mutables ni soportan 2 dimensiones:

```julia-repl
julia> similar(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

Por el contrario, `similar(trues(10,10), 2)` devuelve un `BitVector` no inicializado con dos elementos ya que los `BitArray`s son tanto mutables como pueden soportar arreglos unidimensionales:

```julia-repl
julia> similar(trues(10,10), 2)
2-element BitVector:
 0
 0
```

Sin embargo, dado que los `BitArray`s solo pueden almacenar elementos del tipo [`Bool`](@ref), si solicitas un tipo de elemento diferente, se creará un `Array` regular en su lugar:

```julia-repl
julia> similar(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

Ver también: [`undef`](@ref), [`isassigned`](@ref).
