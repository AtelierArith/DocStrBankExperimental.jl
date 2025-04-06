```
Ref{T}
```

Un objeto que referencia de manera segura datos del tipo `T`. Este tipo está garantizado para apuntar a memoria válida, asignada por Julia, del tipo correcto. Los datos subyacentes están protegidos de ser liberados por el recolector de basura mientras el `Ref` mismo esté referenciado.

En Julia, los objetos `Ref` se desreferencian (cargan o almacenan) con `[]`.

La creación de un `Ref` a un valor `x` del tipo `T` se escribe generalmente como `Ref(x)`. Además, para crear punteros interiores a contenedores (como Array o Ptr), se puede escribir `Ref(a, i)` para crear una referencia al elemento `i`-ésimo de `a`.

`Ref{T}()` crea una referencia a un valor del tipo `T` sin inicialización. Para un tipo de bits `T`, el valor será lo que actualmente resida en la memoria asignada. Para un tipo no de bits `T`, la referencia será indefinida y intentar desreferenciarla resultará en un error, "UndefRefError: acceso a referencia indefinida".

Para verificar si un `Ref` es una referencia indefinida, utiliza [`isassigned(ref::RefValue)`](@ref). Por ejemplo, `isassigned(Ref{T}())` es `false` si `T` no es un tipo de bits. Si `T` es un tipo de bits, `isassigned(Ref{T}())` siempre será verdadero.

Cuando se pasa como un argumento de `ccall` (ya sea como un tipo `Ptr` o `Ref`), un objeto `Ref` se convertirá en un puntero nativo a los datos que referencia. Para la mayoría de los `T`, o cuando se convierte a un `Ptr{Cvoid}`, este es un puntero a los datos del objeto. Cuando `T` es un tipo `isbits`, este valor puede ser mutado de manera segura, de lo contrario, la mutación es un comportamiento estrictamente indefinido.

Como un caso especial, establecer `T = Any` causará en su lugar la creación de un puntero a la referencia misma cuando se convierta a un `Ptr{Any}` (un `jl_value_t const* const*` si T es inmutable, de lo contrario un `jl_value_t *const *`). Cuando se convierte a un `Ptr{Cvoid}`, seguirá devolviendo un puntero a la región de datos como para cualquier otro `T`.

Una instancia `C_NULL` de `Ptr` puede ser pasada a un argumento `Ref` de `ccall` para inicializarlo.

# Uso en broadcasting

`Ref` a veces se utiliza en broadcasting para tratar los valores referenciados como un escalar.

# Ejemplos

```jldoctest
julia> r = Ref(5) # Crear un Ref con un valor inicial
Base.RefValue{Int64}(5)

julia> r[] # Obtener un valor de un Ref
5

julia> r[] = 7 # Almacenar un nuevo valor en un Ref
7

julia> r # El Ref ahora contiene 7
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # Tratar los valores de referencia como escalares durante el broadcasting
3-element BitVector:
 1
 0
 0

julia> Ref{Function}()  # Referencia indefinida a un tipo no de bits, Function
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # Desreferenciar una referencia indefinida resultará en un error
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # Una referencia a un tipo de bits se refiere a un valor indeterminado si no se le da

julia> isassigned(Ref{Int64}()) # Una referencia a un tipo de bits siempre está asignada
true
```
