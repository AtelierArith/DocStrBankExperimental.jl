# Reflection and introspection

Julia proporciona una variedad de capacidades de reflexión en tiempo de ejecución.

## Module bindings

Los nombres públicos para un `Module` están disponibles usando [`names(m::Module)`](@ref), que devolverá un array de elementos [`Symbol`](@ref) que representan los enlaces públicos. `names(m::Module, all = true)` devuelve símbolos para todos los enlaces en `m`, independientemente del estado público.

## DataType fields

Los nombres de los campos de `DataType` pueden ser interrogados usando [`fieldnames`](@ref). Por ejemplo, dado el siguiente tipo, `fieldnames(Point)` devuelve una tupla de [`Symbol`](@ref) que representan los nombres de los campos:

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

El tipo de cada campo en un objeto `Point` se almacena en el campo `types` de la variable `Point` misma:

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

Mientras `x` está anotado como un `Int`, `y` no fue anotado en la definición de tipo, por lo tanto, `y` por defecto es del tipo `Any`.

Los tipos se representan a sí mismos como una estructura llamada `DataType`:

```jldoctest struct_point
julia> typeof(Point)
DataType
```

Tenga en cuenta que `fieldnames(DataType)` da los nombres de cada campo de `DataType` en sí, y uno de estos campos es el campo `types` observado en el ejemplo anterior.

## Subtypes

Los *subtipos* directos de cualquier `DataType` pueden ser listados usando [`subtypes`](@ref). Por ejemplo, el `DataType` abstracto [`AbstractFloat`](@ref) tiene cuatro (concretos) subtipos:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

Cualquier subtipo abstracto también se incluirá en esta lista, pero no se incluirán subtipos adicionales de los mismos; se puede utilizar la aplicación recursiva de [`subtypes`](@ref) para inspeccionar el árbol de tipos completo.

Tenga en cuenta que [`subtypes`](@ref) se encuentra dentro de [`InteractiveUtils`](@ref man-interactive-utils), pero se exporta automáticamente al usar el REPL.

## DataType layout

La representación interna de un `DataType` es críticamente importante al interactuar con código C y varias funciones están disponibles para inspeccionar estos detalles. [`isbitstype(T::DataType)`](@ref) devuelve verdadero si `T` se almacena con alineación compatible con C. [`fieldoffset(T::DataType, i::Integer)`](@ref) devuelve el desplazamiento (en bytes) para el campo *i* relativo al inicio del tipo.

## Function methods

Los métodos de cualquier función genérica pueden ser listados usando [`methods`](@ref). La tabla de despacho de métodos puede ser buscada para métodos que acepten un tipo dado usando [`methodswith`](@ref).

## Expansion and lowering

Como se discutió en la sección [Metaprogramming](@ref), la función [`macroexpand`](@ref) proporciona la expresión no citada e interpolada ([`Expr`](@ref)) en forma para un macro dado. Para usar `macroexpand`, cita el bloque de expresión en sí (¡de lo contrario, el macro será evaluado y el resultado será pasado en su lugar!). Por ejemplo:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

Las funciones `Base.Meta.show_sexpr` y [`dump`](@ref) se utilizan para mostrar vistas en estilo S-exp y vistas de detalles anidadas en profundidad para cualquier expresión.

Finalmente, la función [`Meta.lower`](@ref) proporciona la forma `lowered` de cualquier expresión y es de particular interés para entender cómo los constructos del lenguaje se mapean a operaciones primitivas como asignaciones, ramas y llamadas:

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

Inspeccionar la forma reducida para funciones requiere la selección del método específico a mostrar, porque las funciones genéricas pueden tener muchos métodos con diferentes firmas de tipo. Para este propósito, el código de reducción específico del método está disponible usando [`code_lowered`](@ref), y la forma inferida por tipo está disponible usando [`code_typed`](@ref). [`code_warntype`](@ref) añade resaltado a la salida de `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566`.

Más cerca de la máquina, la representación intermedia de LLVM de una función se puede imprimir usando [`code_llvm`](@ref), y finalmente el código de máquina compilado está disponible usando [`code_native`](@ref) (esto activará la compilación JIT/generación de código para cualquier función que no haya sido llamada previamente).

Para conveniencia, hay versiones macro de las funciones anteriores que toman llamadas de función estándar y expanden los tipos de argumentos automáticamente:

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

Para más información, consulte [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_warntype`](@ref), [`@code_llvm`](@ref), y [`@code_native`](@ref).

### Printing of debug information

Las funciones y macros mencionadas anteriormente toman el argumento de palabra clave `debuginfo` que controla el nivel de información de depuración impresa.

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

Los valores posibles para `debuginfo` son: `:none`, `:source` y `:default`. Por defecto, la información de depuración no se imprime, pero eso se puede cambiar configurando `Base.IRShow.default_debuginfo[] = :source`.
