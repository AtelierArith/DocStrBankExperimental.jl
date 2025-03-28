# Base.Cartesian

Le module (non exporté) Cartesian fournit des macros qui facilitent l'écriture d'algorithmes multidimensionnels. Le plus souvent, vous pouvez écrire de tels algorithmes avec [straightforward techniques](https://julialang.org/blog/2016/02/iteration); cependant, il existe quelques cas où `Base.Cartesian` est encore utile ou nécessaire.

## Principles of usage

Un exemple simple d'utilisation est :

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

qui génère le code suivant :

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

En général, Cartesian vous permet d'écrire du code générique contenant des éléments répétitifs, comme les boucles imbriquées dans cet exemple. D'autres applications incluent des expressions répétées (par exemple, le déroulement de boucle) ou la création d'appels de fonction avec un nombre variable d'arguments sans utiliser la construction "splat" (`i...`).

## Basic syntax

La syntaxe (de base) de `@nloops` est la suivante :

  * Le premier argument doit être un entier (*pas* une variable) spécifiant le nombre de boucles.
  * Le deuxième argument est le préfixe de symbole utilisé pour la variable d'itération. Ici, nous avons utilisé `i`, et les variables `i_1, i_2, i_3` ont été générées.
  * Le troisième argument spécifie la plage pour chaque variable d'itérateur. Si vous utilisez une variable (symbole) ici, elle est considérée comme `axes(A, dim)`. Plus flexiblement, vous pouvez utiliser la syntaxe d'expression de fonction anonyme décrite ci-dessous.
  * Le dernier argument est le corps de la boucle. Ici, c'est ce qui apparaît entre `begin...end`.

Il existe des fonctionnalités supplémentaires de `@nloops` décrites dans le [reference section](@ref dev-cartesian-reference).

`@nref` suit un modèle similaire, générant `A[i_1,i_2,i_3]` à partir de `@nref 3 A i`. La pratique générale est de lire de gauche à droite, c'est pourquoi `@nloops` est `@nloops 3 i A expr` (comme dans `for i_2 = axes(A, 2)`, où `i_2` est à gauche et la plage est à droite) tandis que `@nref` est `@nref 3 A i` (comme dans `A[i_1,i_2,i_3]`, où le tableau vient en premier).

Si vous développez du code avec Cartesian, vous constaterez peut-être que le débogage est plus facile lorsque vous examinez le code généré, en utilisant `@macroexpand` :

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

Le premier argument de ces deux macros est le nombre d'expressions, qui doit être un entier. Lorsque vous écrivez une fonction que vous souhaitez faire fonctionner dans plusieurs dimensions, ce n'est peut-être pas quelque chose que vous voulez coder en dur. L'approche recommandée est d'utiliser une `@generated function`. Voici un exemple :

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

Naturellement, vous pouvez également préparer des expressions ou effectuer des calculs avant le bloc `quote`.

### Anonymous-function expressions as macro arguments

Peut-être la fonctionnalité la plus puissante de `Cartesian` est la capacité de fournir des expressions de fonction anonyme qui sont évaluées au moment de l'analyse. Considérons un exemple simple :

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs` génère `n` expressions qui suivent un modèle. Ce code générerait les déclarations suivantes :

```julia
i_1 = 1
i_2 = 1
```

Dans chaque déclaration générée, un `j` "isolé" (la variable de la fonction anonyme) est remplacé par des valeurs dans la plage `1:2`. En général, Cartesian utilise une syntaxe similaire à LaTeX. Cela vous permet de faire des calculs sur l'index `j`. Voici un exemple de calcul des pas d'un tableau :

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

générer des expressions

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

Les expressions de fonction anonyme ont de nombreuses utilisations en pratique.

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
