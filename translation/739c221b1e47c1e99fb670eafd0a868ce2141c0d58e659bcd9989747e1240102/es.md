```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

La generación de números aleatorios en Julia utiliza el algoritmo [Xoshiro256++](https://prng.di.unimi.it/) por defecto, con estado por `Task`. Otros tipos de RNG se pueden integrar heredando el tipo `AbstractRNG`; luego se pueden usar para obtener múltiples flujos de números aleatorios.

Los PRNGs (generadores de números seudoaleatorios) exportados por el paquete `Random` son:

  * `TaskLocalRNG`: un token que representa el uso del flujo local de tarea actualmente activo, sembrado de manera determinista a partir de la tarea padre, o por `RandomDevice` (con aleatoriedad del sistema) al inicio del programa.
  * `Xoshiro`: genera un flujo de números aleatorios de alta calidad con un pequeño vector de estado y un alto rendimiento utilizando el algoritmo Xoshiro256++
  * `RandomDevice`: para la entropía proporcionada por el sistema operativo. Esto puede ser utilizado para números aleatorios criptográficamente seguros (CS(P)RNG).
  * `MersenneTwister`: un generador de números aleatorios de alta calidad alternativo que era el predeterminado en versiones anteriores de Julia, y también es bastante rápido, pero requiere mucho más espacio para almacenar el vector de estado y generar una secuencia aleatoria.

La mayoría de las funciones relacionadas con la generación aleatoria aceptan un objeto `AbstractRNG` opcional como primer argumento. Algunas también aceptan especificaciones de dimensiones `dims...` (que también se pueden dar como una tupla) para generar arreglos de valores aleatorios. En un programa multihilo, generalmente deberías usar diferentes objetos RNG de diferentes hilos o tareas para ser seguro en cuanto a hilos. Sin embargo, el RNG predeterminado es seguro para hilos a partir de Julia 1.3 (utilizando un RNG por hilo hasta la versión 1.6, y por tarea a partir de entonces).

Los RNG proporcionados pueden generar números aleatorios uniformes de los siguientes tipos: [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref), [`BigFloat`](@ref), [`Bool`](@ref), [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`BigInt`](@ref) (o números complejos de esos tipos). Los números de punto flotante aleatorios se generan uniformemente en $[0, 1)$. Como `BigInt` representa enteros sin límites, el intervalo debe ser especificado (por ejemplo, `rand(big.(1:6))`).

Además, las distribuciones normal y exponencial están implementadas para algunos tipos de `AbstractFloat` y `Complex`, consulta [`randn`](@ref) y [`randexp`](@ref) para más detalles.

Para generar números aleatorios de otras distribuciones, consulte el paquete [Distributions.jl](https://juliastats.org/Distributions.jl/stable/).

!!! warning
    Debido a que la forma precisa en que se generan los números aleatorios se considera un detalle de implementación, las correcciones de errores y las mejoras de velocidad pueden cambiar la secuencia de números que se generan después de un cambio de versión. Por lo tanto, se desaconseja confiar en una semilla específica o en una secuencia generada de números durante las pruebas unitarias; en su lugar, considere probar las propiedades de los métodos en cuestión.


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

Hay dos formas mayormente ortogonales de extender las funcionalidades de `Random`:

1. generando valores aleatorios de tipos personalizados
2. creando nuevos generadores

La API para 1) es bastante funcional, pero es relativamente reciente, por lo que aún puede tener que evolucionar en lanzamientos posteriores del módulo `Random`. Por ejemplo, generalmente es suficiente implementar un método `rand` para que todos los demás métodos habituales funcionen automáticamente.

La API para 2) sigue siendo rudimentaria y puede requerir más trabajo del estrictamente necesario por parte del implementador, para poder soportar los tipos habituales de valores generados.

### Generating random values of custom types

Generar valores aleatorios para algunas distribuciones puede implicar varios compromisos. *Valores precomputados*, como un [alias table](https://en.wikipedia.org/wiki/Alias_method) para distribuciones discretas, o [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling) para distribuciones univariadas, pueden acelerar considerablemente el muestreo. Cuánta información debe ser precomputada puede depender del número de valores que planeamos extraer de una distribución. Además, algunos generadores de números aleatorios pueden tener ciertas propiedades que varios algoritmos pueden querer explotar.

El módulo `Random` define un marco personalizable para obtener valores aleatorios que puede abordar estos problemas. Cada invocación de `rand` genera un *muestreador* que se puede personalizar teniendo en cuenta los compromisos mencionados anteriormente, añadiendo métodos a `Sampler`, que a su vez puede despachar sobre el generador de números aleatorios, el objeto que caracteriza la distribución y una sugerencia para el número de repeticiones. Actualmente, para este último, se utilizan `Val{1}` (para una sola muestra) y `Val{Inf}` (para un número arbitrario), siendo `Random.Repetition` un alias para ambos.

El objeto devuelto por `Sampler` se utiliza para generar los valores aleatorios. Al implementar la interfaz de generación aleatoria para un valor `X` que se puede muestrear, el implementador debe definir el método

```julia
rand(rng, sampler)
```

para el `sampler` particular devuelto por `Sampler(rng, X, repetition)`.

Los muestreadores pueden ser valores arbitrarios que implementan `rand(rng, sampler)`, pero para la mayoría de las aplicaciones, los siguientes muestreadores predefinidos pueden ser suficientes:

1. `SamplerType{T}()` se puede utilizar para implementar muestreadores que extraen del tipo `T` (por ejemplo, `rand(Int)`). Este es el valor predeterminado devuelto por `Sampler` para *tipos*.
2. `SamplerTrivial(self)` es un simple envoltorio para `self`, que se puede acceder con `[]`. Este es el muestreador recomendado cuando no se necesita información precomputada (por ejemplo, `rand(1:3)`), y es el valor predeterminado devuelto por `Sampler` para *valores*.
3. `SamplerSimple(self, data)` también contiene el campo adicional `data`, que se puede utilizar para almacenar valores precomputados arbitrarios, que deben ser calculados en un *método personalizado* de `Sampler`.

Proporcionamos ejemplos para cada uno de estos. Asumimos aquí que la elección del algoritmo es independiente del RNG, por lo que usamos `AbstractRNG` en nuestras firmas.

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

Desacoplar la precomputación de la generación real de los valores es parte de la API y también está disponible para el usuario. Como ejemplo, supongamos que `rand(rng, 1:20)` tiene que ser llamado repetidamente en un bucle: la forma de aprovechar este desacoplamiento es la siguiente:

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

Este es el mecanismo que también se utiliza en la biblioteca estándar, por ejemplo, en la implementación predeterminada de generación de arreglos aleatorios (como en `rand(1:20, 10)`).

#### Generating values from a type

Dado un tipo `T`, actualmente se asume que si `rand(T)` está definido, se producirá un objeto del tipo `T`. `SamplerType` es el *muestreador predeterminado para tipos*. Para definir la generación aleatoria de valores del tipo `T`, se debe definir el método `rand(rng::AbstractRNG, ::Random.SamplerType{T})`, y debe devolver valores que se espera que devuelva `rand(rng, T)`.

Tomemos el siguiente ejemplo: implementamos un tipo `Die`, con un número variable `n` de lados, numerados del `1` al `n`. Queremos que `rand(Die)` produzca un `Die` con un número aleatorio de hasta 20 lados (y al menos 4):

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

Los métodos escalares y de matriz para `Die` ahora funcionan como se esperaba:

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

Aquí definimos un muestreador para una colección. Si no se requieren datos precomputados, se puede implementar con un muestreador `SamplerTrivial`, que de hecho es el *fallback predeterminado para valores*.

Para definir la generación aleatoria a partir de objetos del tipo `S`, se debe definir el siguiente método: `rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`. Aquí, `sp` simplemente envuelve un objeto del tipo `S`, que se puede acceder a través de `sp[]`. Continuando con el ejemplo del `Die`, ahora queremos definir `rand(d::Die)` para producir un `Int` correspondiente a uno de los lados de `d`:

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

Dada un tipo de colección `S`, actualmente se asume que si `rand(::S)` está definido, se producirá un objeto del tipo `eltype(S)`. En el último ejemplo, se produce un `Vector{Any}`; la razón es que `eltype(Die) == Any`. La solución es definir `Base.eltype(::Type{Die}) = Int`.

#### Generating values for an `AbstractFloat` type

Los tipos `AbstractFloat` son tratados de manera especial, porque por defecto no se producen valores aleatorios en todo el dominio del tipo, sino más bien en `[0,1)`. El siguiente método debe ser implementado para `T <: AbstractFloat`: `Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

Considere una distribución discreta, donde los números `1:n` se extraen con probabilidades dadas que suman uno. Cuando se necesitan muchos valores de esta distribución, el método más rápido es usar un [alias table](https://en.wikipedia.org/wiki/Alias_method). No proporcionamos el algoritmo para construir tal tabla aquí, pero supongamos que está disponible en `make_alias_table(probabilities)` en su lugar, y `draw_number(rng, alias_table)` se puede usar para extraer un número aleatorio de ella.

Supongamos que la distribución está descrita por

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

y que *siempre* queremos construir una tabla de alias, independientemente del número de valores necesarios (aprendemos a personalizar esto a continuación). Los métodos

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

debe definirse para devolver un muestreador con datos precomputados, luego

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

se utilizará para dibujar los valores.

#### Custom sampler types

El tipo `SamplerSimple` es suficiente para la mayoría de los casos de uso con datos precomputados. Sin embargo, para demostrar cómo usar tipos de muestreador personalizados, aquí implementamos algo similar a `SamplerSimple`.

Volviendo a nuestro ejemplo de `Die`: `rand(::Die)` utiliza generación aleatoria de un rango, por lo que hay una oportunidad para esta optimización. Llamamos a nuestro muestreador personalizado `SamplerDie`.

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

Ahora es posible obtener un muestreador con `sp = Sampler(rng, die)`, y usar `sp` en lugar de `die` en cualquier llamada a `rand` que involucre `rng`. En el ejemplo simplista anterior, `die` no necesita ser almacenado en `SamplerDie`, pero esto es a menudo el caso en la práctica.

Por supuesto, este patrón es tan frecuente que el tipo de ayudante utilizado arriba, a saber, `Random.SamplerSimple`, está disponible, ahorrándonos la definición de `SamplerDie`: podríamos haber implementado nuestro desacoplamiento con:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

Aquí, `sp.data` se refiere al segundo parámetro en la llamada al constructor `SamplerSimple` (en este caso igual a `Sampler(rng, 1:die.nsides, r)`), mientras que el objeto `Die` se puede acceder a través de `sp[]`.

Como `SamplerDie`, cualquier muestreador personalizado debe ser un subtipo de `Sampler{T}` donde `T` es el tipo de los valores generados. Tenga en cuenta que `SamplerSimple(x, data) isa Sampler{eltype(x)}`, por lo que esto restringe lo que el primer argumento de `SamplerSimple` puede ser (se recomienda usar `SamplerSimple` como en el ejemplo de `Die`, donde `x` se reenvía simplemente al definir un método `Sampler`). De manera similar, `SamplerTrivial(x) isa Sampler{eltype(x)}`.

Otro tipo de ayudante está actualmente disponible para otros casos, `Random.SamplerTag`, pero se considera una API interna y puede romperse en cualquier momento sin las debidas deprecaciones.

#### Using distinct algorithms for scalar or array generation

En algunos casos, si uno quiere generar solo un puñado de valores o un gran número de valores tendrá un impacto en la elección del algoritmo. Esto se maneja con el tercer parámetro del constructor `Sampler`. Supongamos que definimos dos tipos auxiliares para `Die`, digamos `SamplerDie1` que debería usarse para generar solo unos pocos valores aleatorios, y `SamplerDieMany` para muchos valores. Podemos usar esos tipos de la siguiente manera:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

Por supuesto, `rand` también debe estar definido en esos tipos (es decir, `rand(::AbstractRNG, ::SamplerDie1)` y `rand(::AbstractRNG, ::SamplerDieMany)`). Tenga en cuenta que, como de costumbre, `SamplerTrivial` y `SamplerSimple` se pueden usar si no son necesarios tipos personalizados.

Nota: `Sampler(rng, x)` es simplemente una abreviatura para `Sampler(rng, x, Val(Inf))`, y `Random.Repetition` es un alias para `Union{Val{1}, Val{Inf}}`.

### Creating new generators

La API aún no está claramente definida, pero como regla general:

1. cualquier método `rand` que produzca tipos "básicos" (`isbitstype` tipos enteros y de punto flotante en `Base`) debe definirse para este RNG específico, si son necesarios;
2. otros métodos documentados de `rand` que aceptan un `AbstractRNG` deberían funcionar sin problemas, (siempre que se implementen los métodos de 1) de los que se depende), pero por supuesto pueden ser especializados para este RNG si hay espacio para optimización;
3. `copy` para pseudo-RNGs debe devolver una copia independiente que genere la misma secuencia aleatoria que el original a partir de ese punto cuando se llame de la misma manera. Cuando esto no sea factible (por ejemplo, RNGs basados en hardware), `copy` no debe ser implementado.

Con respecto a 1), un método `rand` puede funcionar automáticamente, pero no está oficialmente soportado y puede romperse sin advertencias en una versión posterior.

Para definir un nuevo método `rand` para un generador hipotético `MyRNG`, y una especificación de valor `s` (por ejemplo, `s == Int`, o `s == 1:10`) de tipo `S==typeof(s)` o `S==Type{s}` si `s` es un tipo, se deben definir los mismos dos métodos que vimos antes:

1. `Sampler(::Tipo{MyRNG}, ::S, ::Repetición)`, que devuelve un objeto de tipo, digamos, `SamplerS`
2. `rand(rng::MyRNG, sp::SamplerS)`

Puede suceder que `Sampler(rng::AbstractRNG, ::S, ::Repetition)` ya esté definido en el módulo `Random`. En ese caso, sería posible omitir el paso 1) en la práctica (si se desea especializar la generación para este tipo particular de RNG), pero el tipo correspondiente `SamplerS` se considera un detalle interno y puede cambiar sin previo aviso.

#### Specializing array generation

En algunos casos, para un tipo de RNG dado, generar un array de valores aleatorios puede ser más eficiente con un método especializado que simplemente utilizando la técnica de desacoplamiento explicada anteriormente. Este es, por ejemplo, el caso de `MersenneTwister`, que escribe de forma nativa valores aleatorios en un array.

Para implementar esta especialización para `MyRNG` y para una especificación `s`, produciendo elementos del tipo `S`, se puede definir el siguiente método: `rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`, donde `SamplerS` es el tipo del muestreador devuelto por `Sampler(MyRNG, s, Val(Inf))`. En lugar de `AbstractArray`, es posible implementar la funcionalidad solo para un subtipo, por ejemplo, `Array{S}`. El método de array no mutante de `rand` llamará automáticamente a esta especialización internamente.

```@meta
DocTestSetup = nothing
```

# Reproducibility

Al utilizar un parámetro RNG inicializado con una semilla dada, puedes reproducir la misma secuencia de números pseudorandom cuando ejecutas tu programa múltiples veces. Sin embargo, una versión menor de Julia (por ejemplo, de 1.3 a 1.4) *puede cambiar* la secuencia de números pseudorandom generados a partir de una semilla específica, en particular si se utiliza `MersenneTwister`. (Incluso si la secuencia producida por una función de bajo nivel como [`rand`](@ref) no cambia, la salida de funciones de nivel superior como [`randsubseq`](@ref) puede cambiar debido a actualizaciones de algoritmos.) Razonamiento: garantizar que los flujos pseudorandom nunca cambien prohíbe muchas mejoras algorítmicas.

Si necesitas garantizar la reproducibilidad exacta de datos aleatorios, es aconsejable *guardar los datos* (por ejemplo, como un archivo adjunto suplementario en una publicación científica). (También puedes, por supuesto, especificar una versión particular de Julia y un manifiesto de paquetes, especialmente si requieres reproducibilidad a nivel de bits.)

Las pruebas de software que dependen de datos "aleatorios" *específicos* también deberían, en general, guardar los datos, incrustarlos en el código de prueba o utilizar paquetes de terceros como [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl). Por otro lado, las pruebas que deberían pasar para la mayoría de los datos aleatorios (por ejemplo, probar `A \ (A*x) ≈ x` para una matriz aleatoria `A = randn(n,n)`) pueden usar un generador de números aleatorios (RNG) con una semilla fija para asegurar que simplemente ejecutar la prueba muchas veces no encuentre un fallo debido a datos muy improbables (por ejemplo, una matriz extremadamente mal condicionada).

La *distribución* estadística de la cual se extraen muestras aleatorias *está* garantizada que sea la misma en cualquier versión menor de Julia.
