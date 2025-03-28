```
où
```

Le mot-clé `où` crée un type [`UnionAll`](@ref), qui peut être considéré comme une union itérée d'autres types, sur toutes les valeurs d'une certaine variable. Par exemple, `Vector{T} où T<:Real` inclut tous les [`Vector`](@ref)s où le type d'élément est une sorte de nombre `Real`.

La liaison de variable par défaut est [`Any`](@ref) si elle est omise :

```julia
Vector{T} où T    # abréviation pour `où T<:Any`
```

Les variables peuvent également avoir des bornes inférieures :

```julia
Vector{T} où T>:Int
Vector{T} où Int<:T<:Real
```

Il existe également une syntaxe concise pour les expressions `où` imbriquées. Par exemple, ceci :

```julia
Pair{T, S} où S<:Array{T} où T<:Number
```

peut être abrégé en :

```julia
Pair{T, S} où {T<:Number, S<:Array{T}}
```

Cette forme se trouve souvent dans les signatures de méthode.

Notez que dans cette forme, les variables sont listées dans l'ordre extérieur d'abord. Cela correspond à l'ordre dans lequel les variables sont substituées lorsque un type est "appliqué" à des valeurs de paramètres en utilisant la syntaxe `T{p1, p2, ...}`.
