# Calling C and Fortran Code

Bien que la plupart du code puisse être écrit en Julia, il existe de nombreuses bibliothèques de haute qualité et matures pour le calcul numérique déjà écrites en C et Fortran. Pour permettre une utilisation facile de ce code existant, Julia rend simple et efficace l'appel des fonctions C et Fortran. Julia a une philosophie de "pas de code standard" : les fonctions peuvent être appelées directement depuis Julia sans aucun code "de liaison", génération de code ou compilation – même depuis l'invite interactive. Cela est réalisé simplement en effectuant un appel approprié avec le macro [`@ccall`](@ref) (ou la syntaxe moins pratique [`ccall`](@ref), voir le [`ccall` syntax section](@ref ccall-interface)).

Le code à appeler doit être disponible en tant que bibliothèque partagée. La plupart des bibliothèques C et Fortran sont déjà livrées compilées en tant que bibliothèques partagées, mais si vous compilez le code vous-même en utilisant GCC (ou Clang), vous devrez utiliser les options `-shared` et `-fPIC`. Les instructions machine générées par le JIT de Julia sont les mêmes que celles d'un appel C natif, donc la surcharge résultante est la même que celle d'un appel à une fonction de bibliothèque depuis du code C. [^1]

Par défaut, les compilateurs Fortran [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran) (par exemple, en convertissant les noms de fonction en minuscules ou en majuscules, souvent en ajoutant un soulignement), et donc pour appeler une fonction Fortran, vous devez passer l'identifiant manglé correspondant à la règle suivie par votre compilateur Fortran. De plus, lors de l'appel d'une fonction Fortran, toutes les entrées doivent être passées en tant que pointeurs vers des valeurs allouées sur le tas ou la pile. Cela s'applique non seulement aux tableaux et autres objets mutables qui sont normalement alloués sur le tas, mais aussi aux valeurs scalaires telles que les entiers et les flottants qui sont normalement alloués sur la pile et souvent passés dans des registres lors de l'utilisation des conventions d'appel C ou Julia.

La syntaxe pour [`@ccall`](@ref) pour générer un appel à la fonction de bibliothèque est :

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

où `library` est une constante ou un littéral de chaîne (mais voir [Non-constant Function Specifications](@ref) ci-dessous). La bibliothèque peut être omise, auquel cas le nom de la fonction est résolu dans le processus actuel. Cette forme peut être utilisée pour appeler des fonctions de bibliothèque C, des fonctions dans l'environnement d'exécution Julia, ou des fonctions dans une application liée à Julia. Le chemin complet vers la bibliothèque peut également être spécifié. Alternativement, `@ccall` peut également être utilisé pour appeler un pointeur de fonction `$function_pointer`, tel qu'un retourné par `Libdl.dlsym`. Les `argtype`s correspondent à la signature de la fonction C et les `argvalue`s sont les valeurs réelles des arguments à passer à la fonction.

!!! note
    Voir ci-dessous comment [map C types to Julia types](@ref mapping-c-types-to-julia).


En tant qu'exemple complet mais simple, ce qui suit appelle la fonction `clock` de la bibliothèque standard C sur la plupart des systèmes dérivés d'Unix :

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock` ne prend aucun argument et renvoie un `Int32`. Pour appeler la fonction `getenv` afin d'obtenir un pointeur vers la valeur d'une variable d'environnement, on effectue un appel comme ceci :

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

En pratique, surtout lorsqu'il s'agit de fournir une fonctionnalité réutilisable, on enveloppe généralement les utilisations de `@ccall` dans des fonctions Julia qui configurent les arguments et vérifient ensuite les erreurs de la manière spécifiée par la fonction C ou Fortran. Et si une erreur se produit, elle est lancée comme une exception Julia normale. Cela est particulièrement important puisque les API C et Fortran sont notoirement incohérentes quant à la manière dont elles indiquent les conditions d'erreur. Par exemple, la fonction de bibliothèque C `getenv` est enveloppée dans la fonction Julia suivante, qui est une version simplifiée de la définition réelle de [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl) :

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

La fonction C `getenv` indique une erreur en retournant `C_NULL`, mais d'autres fonctions standard C indiquent les erreurs de différentes manières, y compris en retournant -1, 0, 1 et d'autres valeurs spéciales. Ce wrapper lance une exception indiquant le problème si l'appelant essaie d'obtenir une variable d'environnement inexistante :

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

Voici un exemple légèrement plus complexe qui découvre le nom d'hôte de la machine locale.

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

Cet exemple alloue d'abord un tableau d'octets. Il appelle ensuite la fonction de la bibliothèque C `gethostname` pour remplir le tableau avec le nom d'hôte. Enfin, il prend un pointeur vers le tampon du nom d'hôte et convertit le pointeur en une chaîne Julia, en supposant qu'il s'agit d'une chaîne C terminée par un caractère nul.

Il est courant que les bibliothèques C utilisent ce modèle qui exige que l'appelant alloue de la mémoire à passer au callee et à remplir. L'allocation de mémoire depuis Julia de cette manière est généralement réalisée en créant un tableau non initialisé et en passant un pointeur vers ses données à la fonction C. C'est pourquoi nous n'utilisons pas le type `Cstring` ici : comme le tableau est non initialisé, il pourrait contenir des octets nuls. La conversion en `Cstring` dans le cadre de l'`@ccall` vérifie la présence d'octets nuls et pourrait donc entraîner une erreur de conversion.

Déréférencer `pointer(hostname)` avec `unsafe_string` est une opération non sécurisée car elle nécessite l'accès à la mémoire allouée pour `hostname` qui a pu être collectée par le ramasse-miettes entre-temps. La macro [`GC.@preserve`](@ref) empêche cela de se produire et donc d'accéder à un emplacement mémoire invalide.

Enfin, voici un exemple de spécification d'une bibliothèque via un chemin. Nous créons une bibliothèque partagée avec le contenu suivant

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

et compilez-le avec `gcc -fPIC -shared -o mylib.so mylib.c`. Il peut ensuite être appelé en spécifiant le chemin (absolu) comme nom de la bibliothèque :

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

Il est possible de passer des fonctions Julia à des fonctions C natives qui acceptent des arguments de type pointeur de fonction. Par exemple, pour correspondre aux prototypes C de la forme :

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

La macro [`@cfunction`](@ref) génère le pointeur de fonction compatible C pour un appel à une fonction Julia. Les arguments de `4d61726b646f776e2e436f64652822222c2022406366756e6374696f6e2229_40726566` sont :

1. Une fonction Julia
2. Le type de retour de la fonction
3. Un tuple de types d'entrée, correspondant à la signature de la fonction

!!! note
    Comme avec `@ccall`, le type de retour et les types d'entrée doivent être des constantes littérales.


!!! note
    Actuellement, seule la convention d'appel C par défaut de la plateforme est prise en charge. Cela signifie que les pointeurs générés par `@cfunction` ne peuvent pas être utilisés dans des appels où WINAPI attend une fonction `stdcall` sur Windows 32 bits, mais peuvent être utilisés sur WIN64 (où `stdcall` est unifié avec la convention d'appel C).


!!! note
    Les fonctions de rappel exposées via `@cfunction` ne doivent pas générer d'erreurs, car cela renverra le contrôle à l'exécution de Julia de manière inattendue et pourrait laisser le programme dans un état indéfini.


Un exemple classique est la fonction `qsort` de la bibliothèque standard C, déclarée comme suit :

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

L'argument `base` est un pointeur vers un tableau de longueur `nitems`, avec des éléments de `size` octets chacun. `compare` est une fonction de rappel qui prend des pointeurs vers deux éléments `a` et `b` et retourne un entier inférieur/supérieur à zéro si `a` doit apparaître avant/après `b` (ou zéro si tout ordre est permis).

Maintenant, supposons que nous avons un tableau 1-d `A` de valeurs en Julia que nous voulons trier en utilisant la fonction `qsort` (plutôt que la fonction `sort` intégrée de Julia). Avant de considérer l'appel de `qsort` et de passer des arguments, nous devons écrire une fonction de comparaison :

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort` attend une fonction de comparaison qui retourne un `int` en C, donc nous annotons le type de retour comme étant `Cint`.

Pour passer cette fonction à C, nous obtenons son adresse en utilisant la macro `@cfunction` :

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref) nécessite trois arguments : la fonction Julia (`mycompare`), le type de retour (`Cint`), et un tuple littéral des types d'arguments d'entrée, dans ce cas pour trier un tableau d'éléments `Cdouble` ([`Float64`](@ref)).

L'appel final à `qsort` ressemble à ceci :

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

Comme l'exemple le montre, le tableau Julia original `A` a maintenant été trié : `[-2.7, 1.3, 3.1, 4.4]`. Notez que Julia [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)), calculant la taille du type d'élément en octets, et ainsi de suite.

Pour le plaisir, essayez d'insérer une ligne `println("mycompare($a, $b)")` dans `mycompare`, ce qui vous permettra de voir les comparaisons que `qsort` effectue (et de vérifier qu'il appelle vraiment la fonction Julia que vous lui avez passée).

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

Il est essentiel de faire correspondre exactement le type C déclaré avec sa déclaration en Julia. Les incohérences peuvent entraîner un code qui fonctionne correctement sur un système mais échoue ou produit des résultats indéterminés sur un autre système.

Notez qu'aucun fichier d'en-tête C n'est utilisé à aucun moment dans le processus d'appel des fonctions C : vous êtes responsable de vous assurer que vos types Julia et vos signatures d'appel reflètent fidèlement ceux du fichier d'en-tête C.[^2]

### [Automatic Type Conversion](@id automatic-type-conversion)

Julia insère automatiquement des appels à la fonction [`Base.cconvert`](@ref) pour convertir chaque argument au type spécifié. Par exemple, l'appel suivant :

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

comportera comme s'il avait été écrit comme ceci :

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref) appelle normalement simplement [`convert`](@ref), mais peut être défini pour retourner un nouvel objet arbitraire plus approprié pour être passé au C. Cela doit être utilisé pour effectuer toutes les allocations de mémoire qui seront accessibles par le code C. Par exemple, cela est utilisé pour convertir un `Array` d'objets (par exemple, des chaînes) en un tableau de pointeurs.

[`Base.unsafe_convert`](@ref) gère la conversion en [`Ptr`](@ref) types. Il est considéré comme dangereux car convertir un objet en un pointeur natif peut cacher l'objet du ramasse-miettes, ce qui peut entraîner sa libération prématurée.

### Type Correspondences

Tout d'abord, examinons quelques termes de type Julia pertinents :

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

Il existe plusieurs types spéciaux à connaître, car aucun autre type ne peut être défini pour se comporter de la même manière :

  * `Float32`

    Correspond exactement au type `float` en C (ou `REAL*4` en Fortran).
  * `Float64`

    Correspond exactement au type `double` en C (ou `REAL*8` en Fortran).
  * `ComplexF32`

    Correspond exactement au type `complex float` en C (ou `COMPLEX*8` en Fortran).
  * `ComplexF64`

    Correspond exactement au type `complex double` en C (ou `COMPLEX*16` en Fortran).
  * `Signé`

    Correspond exactement à l'annotation de type `signed` en C (ou à tout type `INTEGER` en Fortran). Tout type Julia qui n'est pas un sous-type de [`Signed`](@ref) est supposé être non signé.

  * `Ref{T}`

    Comporte comme un `Ptr{T}` qui peut gérer sa mémoire via le GC de Julia.

  * `Array{T,N}`

    Lorsque un tableau est passé à C en tant qu'argument `Ptr{T}`, il n'est pas réinterprété : Julia exige que le type d'élément du tableau corresponde à `T`, et l'adresse du premier élément est passée.

    Par conséquent, si un `Array` contient des données dans le mauvais format, il devra être explicitement converti en utilisant un appel tel que `trunc.(Int32, A)`.

    Pour passer un tableau `A` en tant que pointeur d'un type différent *sans* convertir les données au préalable (par exemple, pour passer un tableau `Float64` à une fonction qui opère sur des octets non interprétés), vous pouvez déclarer l'argument comme `Ptr{Cvoid}`.

    Si un tableau de type `Ptr{T}` est passé comme argument de type `Ptr{Ptr{T}}`, [`Base.cconvert`](@ref) tentera d'abord de créer une copie terminée par un caractère nul du tableau avec chaque élément remplacé par sa version `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566`. Cela permet, par exemple, de passer un tableau de pointeurs `argv` de type `Vector{String}` à un argument de type `Ptr{Ptr{Cchar}}`.

Sur tous les systèmes que nous supportons actuellement, les types de valeur C/C++ de base peuvent être traduits en types Julia comme suit. Chaque type C a également un type Julia correspondant avec le même nom, préfixé par C. Cela peut aider lors de l'écriture de code portable (et à se rappeler qu'un `int` en C n'est pas le même qu'un `Int` en Julia).

**Types indépendants du système**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

Le type [`Cstring`](@ref) est essentiellement un synonyme de `Ptr{UInt8}`, sauf que la conversion en `Cstring` génère une erreur si la chaîne Julia contient des caractères nuls intégrés (ce qui entraînerait une troncature silencieuse de la chaîne si la routine C considère le nul comme le terminateur). Si vous passez un `char*` à une routine C qui ne suppose pas de terminaison nulle (par exemple, parce que vous passez une longueur de chaîne explicite), ou si vous savez avec certitude que votre chaîne Julia ne contient pas de nul et souhaitez ignorer la vérification, vous pouvez utiliser `Ptr{UInt8}` comme type d'argument. `Cstring` peut également être utilisé comme type de retour [`ccall`](@ref), mais dans ce cas, il n'introduit évidemment aucune vérification supplémentaire et est uniquement destiné à améliorer la lisibilité de l'appel.

**Types dépendants du système**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    Lors de l'appel de Fortran, toutes les entrées doivent être passées par des pointeurs vers des valeurs allouées sur le tas ou sur la pile, donc toutes les correspondances de type ci-dessus doivent contenir un wrapper supplémentaire `Ptr{..}` ou `Ref{..}` autour de leur spécification de type.


!!! warning
    Pour les arguments de chaîne (`char*`), le type Julia doit être `Cstring` (si des données terminées par un caractère nul sont attendues), ou soit `Ptr{Cchar}` soit `Ptr{UInt8}` sinon (ces deux types de pointeurs ont le même effet), comme décrit ci-dessus, et non `String`. De même, pour les arguments de tableau (`T[]` ou `T*`), le type Julia doit à nouveau être `Ptr{T}`, et non `Vector{T}`.


!!! warning
    Le type `Char` de Julia fait 32 bits, ce qui n'est pas le même que le type de caractère large (`wchar_t` ou `wint_t`) sur toutes les plateformes.


!!! warning
    Un type de retour `Union{}` signifie que la fonction ne retournera pas, c'est-à-dire `[[noreturn]]` en C++11 ou `_Noreturn` en C11 (par exemple `jl_throw` ou `longjmp`). Ne pas utiliser cela pour les fonctions qui ne retournent aucune valeur (`void`) mais retournent, pour celles-ci, utilisez `Cvoid` à la place.


!!! note
    Pour les arguments `wchar_t*`, le type Julia doit être [`Cwstring`](@ref) (si la routine C attend une chaîne terminée par un caractère nul), ou `Ptr{Cwchar_t}` sinon. Notez également que les données de chaîne UTF-8 en Julia sont en interne terminées par un caractère nul, donc elles peuvent être passées à des fonctions C s'attendant à des données terminées par un caractère nul sans faire de copie (mais l'utilisation du type `Cwstring` entraînera une erreur si la chaîne elle-même contient des caractères nuls).


!!! note
    Les fonctions C qui prennent un argument de type `char**` peuvent être appelées en utilisant un type `Ptr{Ptr{UInt8}}` dans Julia. Par exemple, les fonctions C de la forme :

    ```c
    int main(int argc, char **argv);
    ```

    peut être appelé via le code Julia suivant :

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    Pour les fonctions Fortran prenant des chaînes de longueur variable de type `character(len=*)`, les longueurs de chaîne sont fournies en tant qu'*arguments cachés*. Le type et la position de ces arguments dans la liste sont spécifiques au compilateur, où les fournisseurs de compilateurs utilisent généralement `Csize_t` comme type et ajoutent les arguments cachés à la fin de la liste des arguments. Bien que ce comportement soit fixe pour certains compilateurs (GNU), d'autres *permettent optionnellement* de placer les arguments cachés directement après l'argument de caractère (Intel, PGI). Par exemple, les sous-routines Fortran de la forme

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    peut être appelé via le code Julia suivant, où les longueurs sont ajoutées

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Les compilateurs Fortran *peuvent* également ajouter d'autres arguments cachés pour les pointeurs, les tableaux de forme supposée (`:`) et les tableaux de taille supposée (`*`). Ce comportement peut être évité en utilisant `ISO_C_BINDING` et en incluant `bind(c)` dans la définition de la sous-routine, ce qui est fortement recommandé pour un code interopérable. Dans ce cas, il n'y aura pas d'arguments cachés, au prix de certaines fonctionnalités du langage (par exemple, seul `character(len=1)` sera autorisé pour passer des chaînes).


!!! note
    Une fonction C déclarée pour retourner `Cvoid` renverra la valeur `nothing` en Julia.


### Struct Type Correspondences

Les types composites tels que `struct` en C ou `TYPE` en Fortran90 (ou `STRUCTURE` / `RECORD` dans certaines variantes de F77) peuvent être reproduits en Julia en créant une définition de `struct` avec la même disposition des champs.

Lorsqu'ils sont utilisés de manière récursive, les types `isbits` sont stockés en ligne. Tous les autres types sont stockés comme un pointeur vers les données. Lors de la réflexion d'une structure utilisée par valeur à l'intérieur d'une autre structure en C, il est impératif de ne pas essayer de copier manuellement les champs, car cela ne préservera pas le bon alignement des champs. Au lieu de cela, déclarez un type de structure `isbits` et utilisez-le à la place. Les structures sans nom ne sont pas possibles dans la traduction vers Julia.

Les déclarations de structures et d'unions compactées ne sont pas prises en charge par Julia.

Vous pouvez obtenir une approximation d'un `union` si vous connaissez, a priori, le champ qui aura la plus grande taille (potentiellement en incluant le remplissage). Lorsque vous traduisez vos champs en Julia, déclarez le champ Julia comme étant uniquement de ce type.

Les tableaux de paramètres peuvent être exprimés avec `NTuple`. Par exemple, la structure en notation C est écrite comme

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

peut être écrit en Julia comme

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

Les tableaux de taille inconnue (structures de longueur variable conformes à C99 spécifiées par `[]` ou `[0]`) ne sont pas directement supportés. Souvent, la meilleure façon de gérer cela est de traiter directement les décalages en octets. Par exemple, si une bibliothèque C déclarait un type de chaîne approprié et retournait un pointeur vers celui-ci :

```c
struct String {
    int strlen;
    char data[];
};
```

En Julia, nous pouvons accéder aux parties indépendamment pour faire une copie de cette chaîne :

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

Les arguments de type pour `@ccall` et `@cfunction` sont évalués statiquement, lorsque la méthode contenant l'utilisation est définie. Ils doivent donc prendre la forme d'un tuple littéral, pas d'une variable, et ne peuvent pas référencer des variables locales.

Cela peut sembler une restriction étrange, mais rappelez-vous que, puisque C n'est pas un langage dynamique comme Julia, ses fonctions ne peuvent accepter que des types d'arguments avec une signature fixe, connue statiquement.

Cependant, bien que la disposition des types doive être connue statiquement pour calculer l'ABI C prévu, les paramètres statiques de la fonction sont considérés comme faisant partie de cet environnement statique. Les paramètres statiques de la fonction peuvent être utilisés comme paramètres de type dans la signature d'appel, tant qu'ils n'affectent pas la disposition du type. Par exemple, `f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}` est valide, puisque `Ptr` est toujours un type primitif de taille de mot. Mais, `g(x::T) where {T} = @ccall notvalid(x::T)::T` n'est pas valide, car la disposition du type de `T` n'est pas connue statiquement.

### SIMD Values

Remarque : Cette fonctionnalité est actuellement implémentée uniquement sur les plateformes 64 bits x86 et AArch64.

Si une routine C/C++ a un argument ou une valeur de retour qui est un type SIMD natif, le type Julia correspondant est un tuple homogène de `VecElement` qui se mappe naturellement au type SIMD. Plus précisément :

>   * Le tuple doit avoir la même taille que le type SIMD. Par exemple, un tuple représentant un `__m128` sur x86 doit avoir une taille de 16 octets.
>   * Le type d'élément du tuple doit être une instance de `VecElement{T}` où `T` est un type primitif de 1, 2, 4 ou 8 octets.


Par exemple, considérez cette routine C qui utilise des intrinsics AVX :

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

Le code Julia suivant appelle `dist` en utilisant `ccall` :

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

La machine hôte doit disposer des registres SIMD requis. Par exemple, le code ci-dessus ne fonctionnera pas sur des hôtes sans support AVX.

### Memory Ownership

**`malloc`/`free`**

L'allocation et la désallocation de tels objets doivent être gérées par des appels aux routines de nettoyage appropriées dans les bibliothèques utilisées, tout comme dans tout programme C. N'essayez pas de libérer un objet reçu d'une bibliothèque C avec [`Libc.free`](@ref) en Julia, car cela peut entraîner l'appel de la fonction `free` via la mauvaise bibliothèque et provoquer l'abandon du processus. L'inverse (passer un objet alloué en Julia pour être libéré par une bibliothèque externe) est également invalide.

### When to use `T`, `Ptr{T}` and `Ref{T}`

Dans le code Julia enveloppant des appels à des routines C externes, les données ordinaires (non-pointeurs) doivent être déclarées comme étant de type `T` à l'intérieur du `@ccall`, car elles sont passées par valeur. Pour le code C acceptant des pointeurs, [`Ref{T}`](@ref) doit généralement être utilisé pour les types d'arguments d'entrée, permettant l'utilisation de pointeurs vers de la mémoire gérée soit par Julia, soit par C grâce à l'appel implicite à [`Base.cconvert`](@ref). En revanche, les pointeurs retournés par la fonction C appelée doivent être déclarés comme étant de type de sortie [`Ptr{T}`](@ref), reflétant que la mémoire pointée est gérée uniquement par C. Les pointeurs contenus dans des structures C doivent être représentés comme des champs de type `Ptr{T}` au sein des types de structures Julia correspondants conçus pour imiter la structure interne des structures C correspondantes.

Dans le code Julia enveloppant les appels aux routines Fortran externes, tous les arguments d'entrée doivent être déclarés comme de type `Ref{T}`, car Fortran passe toutes les variables par des pointeurs vers des emplacements mémoire. Le type de retour doit être soit `Cvoid` pour les sous-routines Fortran, soit un `T` pour les fonctions Fortran retournant le type `T`.

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

Pour traduire une liste d'arguments C en Julia :

  * `T`, où `T` est l'un des types primitifs : `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` ou l'un de leurs équivalents `typedef`

      * `T`, où `T` est un type de bits Julia équivalent (selon le tableau ci-dessus)
      * si `T` est un `enum`, le type d'argument doit être équivalent à `Cint` ou `Cuint`
      * la valeur de l'argument sera copiée (passée par valeur)
  * `struct T` (y compris typedef à une structure)

      * `T`, où `T` est un type feuille Julia
      * la valeur de l'argument sera copiée (passée par valeur)
  * `void*`

      * dépend de la façon dont ce paramètre est utilisé, d'abord traduire cela au type de pointeur prévu, puis déterminer l'équivalent Julia en utilisant les règles restantes de cette liste
      * cet argument peut être déclaré comme `Ptr{Cvoid}` s'il s'agit vraiment simplement d'un pointeur inconnu
  * `jl_value_t*`

      * `Tout`
      * la valeur de l'argument doit être un objet Julia valide
  * `jl_value_t* const*`

      * `Ref{Tout}`
      * la liste des arguments doit être un objet Julia valide (ou `C_NULL`)
      * ne peut pas être utilisé pour un paramètre de sortie, à moins que l'utilisateur ne puisse organiser séparément la préservation de l'objet par le GC
  * `T*`

      * `Ref{T}`, où `T` est le type Julia correspondant à `T`
      * la valeur de l'argument sera copiée si c'est un type `inlinealloc` (ce qui inclut `isbits` sinon, la valeur doit être un objet Julia valide
  * `T (*)(...)` (par exemple, un pointeur vers une fonction)

      * `Ptr{Cvoid}` (vous devrez peut-être utiliser [`@cfunction`](@ref) explicitement pour créer ce pointeur)
  * `...` (par exemple, un vararg)

      * [pour `ccall`]: `T...`, où `T` est le type Julia unique de tous les arguments restants
      * [pour `@ccall`]: `; va_arg1::T, va_arg2::S, etc`, où `T` et `S` sont le type Julia (c'est-à-dire séparer les arguments réguliers des varargs avec un `;`)
      * actuellement non pris en charge par `@cfunction`
  * `va_arg`

      * non pris en charge par `ccall` ou `@cfunction`

### `@ccall` / `@cfunction` return type translation guide

Pour traduire un type de retour C en Julia :

  * `vide`

      * `Cvoid` (cela renverra l'instance singleton `nothing::Cvoid`)
  * `T`, où `T` est l'un des types primitifs : `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` ou l'un de leurs équivalents `typedef`

      * `T`, où `T` est un type de bits Julia équivalent (selon le tableau ci-dessus)
      * si `T` est un `enum`, le type d'argument doit être équivalent à `Cint` ou `Cuint`
      * la valeur de l'argument sera copiée (retournée par valeur)
  * `struct T` (y compris typedef à une structure)

      * `T`, où `T` est un type de feuille Julia
      * la valeur de l'argument sera copiée (retournée par valeur)
  * `void*`

      * dépend de la façon dont ce paramètre est utilisé, d'abord traduire cela au type de pointeur prévu, puis déterminer l'équivalent Julia en utilisant les règles restantes de cette liste
      * cet argument peut être déclaré comme `Ptr{Cvoid}` s'il s'agit vraiment simplement d'un pointeur inconnu
  * `jl_value_t*`

      * `Tout`
      * la valeur de l'argument doit être un objet Julia valide
  * `jl_value_t**`

      * `Ptr{Any}` (`Ref{Any}` est invalide en tant que type de retour)
  * `T*`

      * Si la mémoire est déjà possédée par Julia, ou est un type `isbits`, et est connue pour être non nulle :

          * `Ref{T}`, où `T` est le type Julia correspondant à `T`
          * un type de retour `Ref{Any}` est invalide, il devrait être soit `Any` (correspondant à `jl_value_t*`) soit `Ptr{Any}` (correspondant à `jl_value_t**`)
          * C **NE DOIT PAS** modifier la mémoire renvoyée via `Ref{T}` si `T` est un type `isbits`
      * Si la mémoire est possédée par C :

          * `Ptr{T}`, où `T` est le type Julia correspondant à `T`
  * `T (*)(...)` (par exemple, un pointeur vers une fonction)

      * `Ptr{Cvoid}` pour appeler cela directement depuis Julia, vous devrez le passer comme premier argument à `@ccall`. Voir [Indirect Calls](@ref).

### Passing Pointers for Modifying Inputs

Parce que C ne prend pas en charge les valeurs de retour multiples, les fonctions C prennent souvent des pointeurs vers des données que la fonction modifiera. Pour accomplir cela dans un `@ccall`, vous devez d'abord encapsuler la valeur à l'intérieur d'un [`Ref{T}`](@ref) du type approprié. Lorsque vous passez cet objet `Ref` en tant qu'argument, Julia passera automatiquement un pointeur C vers les données encapsulées :

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

À son retour, le contenu de `width` et `range` peut être récupéré (s'ils ont été modifiés par `foo`) par `width[]` et `range[]`; c'est-à-dire qu'ils agissent comme des tableaux à zéro dimension.

## C Wrapper Examples

Commençons par un exemple simple d'un wrapper C qui retourne un type `Ptr` :

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

Le [GNU Scientific Library](https://www.gnu.org/software/gsl/) (ici supposé accessible via `:libgsl`) définit un pointeur opaque, `gsl_permutation *`, comme type de retour de la fonction C `gsl_permutation_alloc`. Comme le code utilisateur n'a jamais besoin de regarder à l'intérieur de la structure `gsl_permutation`, le wrapper Julia correspondant a simplement besoin d'une nouvelle déclaration de type, `gsl_permutation`, qui n'a pas de champs internes et dont le seul but est d'être placé dans le paramètre de type d'un type `Ptr`. Le type de retour de [`ccall`](@ref) est déclaré comme `Ptr{gsl_permutation}`, puisque la mémoire allouée et pointée par `output_ptr` est contrôlée par C.

L'entrée `n` est passée par valeur, et donc la signature d'entrée de la fonction est simplement déclarée comme `::Csize_t` sans qu'aucun `Ref` ou `Ptr` ne soit nécessaire. (Si le wrapper appelait une fonction Fortran à la place, la signature d'entrée de la fonction correspondante serait alors `::Ref{Csize_t}`, puisque les variables Fortran sont passées par pointeurs.) De plus, `n` peut être de n'importe quel type convertible en un entier `Csize_t` ; le [`ccall`](@ref) appelle implicitement [`Base.cconvert(Csize_t, n)`](@ref).

Voici un deuxième exemple enveloppant le destructeur correspondant :

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

Voici un troisième exemple de passage des tableaux Julia :

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

La fonction C `wrapped` retourne un code d'erreur entier ; les résultats de l'évaluation réelle de la fonction de Bessel J remplissent le tableau Julia `result_array`. Cette variable est déclarée comme un `Ref{Cdouble}`, car sa mémoire est allouée et gérée par Julia. L'appel implicite à [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref) décompresse le pointeur Julia en une structure de données de tableau Julia dans une forme compréhensible par C.

## Fortran Wrapper Example

L'exemple suivant utilise `ccall` pour appeler une fonction dans une bibliothèque Fortran commune (libBLAS) afin de calculer un produit scalaire. Notez que le mappage des arguments est un peu différent ici que ci-dessus, car nous devons mapper de Julia à Fortran. Pour chaque type d'argument, nous spécifions `Ref` ou `Ptr`. Cette convention de mangling peut être spécifique à votre compilateur Fortran et à votre système d'exploitation et est probablement non documentée. Cependant, envelopper chacun dans un `Ref` (ou `Ptr`, lorsque cela est équivalent) est une exigence fréquente des implémentations de compilateurs Fortran :

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

Lors du passage de données à un `@ccall`, il est préférable d'éviter d'utiliser la fonction [`pointer`](@ref). À la place, définissez une méthode [`Base.cconvert`](@ref) et passez les variables directement au `@ccall`. Le `@ccall` arrange automatiquement que tous ses arguments soient préservés de la collecte des ordures jusqu'à ce que l'appel retourne. Si une API C stocke une référence à la mémoire allouée par Julia, après le retour du `@ccall`, vous devez vous assurer que l'objet reste visible pour le ramasse-miettes. La manière suggérée de le faire est de créer une variable globale de type `Array{Ref,1}` pour conserver ces valeurs jusqu'à ce que la bibliothèque C vous informe qu'elle a terminé avec elles.

Chaque fois que vous avez créé un pointeur vers des données Julia, vous devez vous assurer que les données originales existent jusqu'à ce que vous ayez fini d'utiliser le pointeur. De nombreuses méthodes en Julia telles que [`unsafe_load`](@ref) et [`String`](@ref) font des copies de données au lieu de prendre possession du tampon, de sorte qu'il est sûr de libérer (ou de modifier) les données originales sans affecter Julia. Une exception notable est [`unsafe_wrap`](@ref) qui, pour des raisons de performance, partage (ou peut être invité à prendre possession de) le tampon sous-jacent.

Le ramasse-miettes ne garantit aucun ordre de finalisation. C'est-à-dire que si `a` contenait une référence à `b` et que `a` et `b` sont tous deux destinés à être collectés, il n'y a aucune garantie que `b` soit finalisé après `a`. Si la finalisation correcte de `a` dépend de la validité de `b`, cela doit être géré d'autres manières.

## Non-constant Function Specifications

Dans certains cas, le nom exact ou le chemin de la bibliothèque nécessaire n'est pas connu à l'avance et doit être calculé au moment de l'exécution. Pour gérer de tels cas, la spécification du composant de la bibliothèque peut être un appel de fonction, par exemple `find_blas().dgemm`. L'expression d'appel sera exécutée lorsque le `ccall` lui-même sera exécuté. Cependant, on suppose que l'emplacement de la bibliothèque ne change pas une fois qu'il est déterminé, donc le résultat de l'appel peut être mis en cache et réutilisé. Par conséquent, le nombre de fois que l'expression s'exécute n'est pas spécifié, et le retour de valeurs différentes pour plusieurs appels entraîne un comportement non spécifié.

Si encore plus de flexibilité est nécessaire, il est possible d'utiliser des valeurs calculées comme noms de fonction en passant par [`eval`](@ref) comme suit :

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

Cette expression construit un nom en utilisant `string`, puis substitue ce nom dans une nouvelle expression `@ccall`, qui est ensuite évaluée. Gardez à l'esprit que `eval` n'opère qu'au niveau supérieur, donc dans cette expression, les variables locales ne seront pas disponibles (à moins que leurs valeurs ne soient substituées par `$`). Pour cette raison, `eval` est généralement utilisé uniquement pour former des définitions de niveau supérieur, par exemple lors de l'encapsulation de bibliothèques contenant de nombreuses fonctions similaires. Un exemple similaire peut être construit pour [`@cfunction`](@ref).

Cependant, faire cela sera également très lent et entraînera des fuites de mémoire, donc vous devriez généralement éviter cela et continuer à lire. La section suivante traite de la façon d'utiliser des appels indirects pour atteindre efficacement un effet similaire.

## Indirect Calls

Le premier argument de `@ccall` peut également être une expression évaluée à l'exécution. Dans ce cas, l'expression doit évaluer à un `Ptr`, qui sera utilisé comme l'adresse de la fonction native à appeler. Ce comportement se produit lorsque le premier argument de `@ccall` contient des références à des non-constantes, telles que des variables locales, des arguments de fonction ou des globaux non constants.

Par exemple, vous pourriez rechercher la fonction via `dlsym`, puis la mettre en cache dans une référence partagée pour cette session. Par exemple :

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

Le premier argument de [`@cfunction`](@ref) peut être marqué avec un `$`, auquel cas la valeur de retour sera plutôt un `struct CFunction` qui encapsule l'argument. Vous devez vous assurer que cet objet de retour reste vivant jusqu'à ce que toutes ses utilisations soient terminées. Le contenu et le code au pointeur cfunction seront effacés via un [`finalizer`](@ref) lorsque cette référence sera abandonnée et à la fin du programme. Cela n'est généralement pas nécessaire, puisque cette fonctionnalité n'est pas présente en C, mais peut être utile pour traiter des API mal conçues qui ne fournissent pas de paramètre d'environnement de fermeture séparé.

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    La fermeture [`@cfunction`](@ref) repose sur des trampolines LLVM, qui ne sont pas disponibles sur toutes les plateformes (par exemple ARM et PowerPC).


## Closing a Library

Il est parfois utile de fermer (décharger) une bibliothèque afin qu'elle puisse être rechargée. Par exemple, lors du développement de code C à utiliser avec Julia, il peut être nécessaire de compiler, d'appeler le code C depuis Julia, puis de fermer la bibliothèque, d'apporter une modification, de recompiler et de charger les nouvelles modifications. On peut soit redémarrer Julia, soit utiliser les fonctions `Libdl` pour gérer explicitement la bibliothèque, telles que :

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

Notez que lors de l'utilisation de `@ccall` avec l'entrée (par exemple, `@ccall "./my_lib.so".my_fcn(...)::Cvoid`), la bibliothèque est ouverte implicitement et il se peut qu'elle ne soit pas fermée explicitement.

## Variadic function calls

Pour appeler des fonctions C variadiques, un `point-virgule` peut être utilisé dans la liste des arguments pour séparer les arguments requis des arguments variadiques. Un exemple avec la fonction `printf` est donné ci-dessous :

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

Il existe une autre interface alternative à `@ccall`. Cette interface est légèrement moins pratique mais elle permet de spécifier un [calling convention](@ref calling-convention).

Les arguments de [`ccall`](@ref) sont :

1. Un couple `(:function, "library")` (le plus courant),

    OU

    un symbole de nom de `:function` ou une chaîne de nom `"function"` (pour les symboles dans le processus actuel ou libc),

    OU

    un pointeur de fonction (par exemple, de `dlsym`).
2. Le type de retour de la fonction
3. Un tuple de types d'entrée, correspondant à la signature de la fonction. Une erreur courante est d'oublier qu'un 1-tuple de types d'arguments doit être écrit avec une virgule finale.
4. Les valeurs réelles des arguments à passer à la fonction, le cas échéant ; chacun est un paramètre distinct.

!!! note
    Le couple `(:function, "library")`, le type de retour et les types d'entrée doivent être des constantes littérales (c'est-à-dire qu'ils ne peuvent pas être des variables, mais voir [Non-constant Function Specifications](@ref)).

    Les paramètres restants sont évalués à la compilation, lorsque la méthode contenant est définie.


Une table de traductions entre les interfaces macro et fonction est donnée ci-dessous.

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

Le deuxième argument de `ccall` (immédiatement précédant le type de retour) peut être un spécificateur de convention d'appel en option (le macro `@ccall` ne prend actuellement pas en charge la spécification d'une convention d'appel). Sans spécificateur, la convention d'appel C par défaut de la plateforme est utilisée. Les autres conventions prises en charge sont : `stdcall`, `cdecl`, `fastcall` et `thiscall` (sans effet sur Windows 64 bits). Par exemple (dans `base/libc.jl`), nous voyons le même `gethostname``ccall` que ci-dessus, mais avec la signature correcte pour Windows :

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

Pour plus d'informations, veuillez consulter le [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions).

Il existe une convention d'appel spéciale supplémentaire [`llvmcall`](@ref Base.llvmcall), qui permet d'insérer des appels aux intrinsics LLVM directement. Cela peut être particulièrement utile lors de la cible de plateformes inhabituelles telles que les GPGPUs. Par exemple, pour [CUDA](https://llvm.org/docs/NVPTXUsage.html), nous devons être en mesure de lire l'index du thread :

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

Comme pour tout `ccall`, il est essentiel d'obtenir la signature des arguments exactement correcte. Notez également qu'il n'y a pas de couche de compatibilité qui garantit que l'intrinsèque a du sens et fonctionne sur la cible actuelle, contrairement aux fonctions Julia équivalentes exposées par `Core.Intrinsics`.

## Accessing Global Variables

Les variables globales exportées par les bibliothèques natives peuvent être accessibles par nom en utilisant la fonction [`cglobal`](@ref). Les arguments de `4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566` sont une spécification de symbole identique à celle utilisée par [`ccall`](@ref), et un type décrivant la valeur stockée dans la variable :

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

Le résultat est un pointeur donnant l'adresse de la valeur. La valeur peut être manipulée à travers ce pointeur en utilisant [`unsafe_load`](@ref) et [`unsafe_store!`](@ref).

!!! note
    Ce symbole `errno` peut ne pas être trouvé dans une bibliothèque nommée "libc", car il s'agit d'un détail d'implémentation de votre compilateur système. En général, les symboles de la bibliothèque standard doivent être accessibles simplement par leur nom, permettant au compilateur de remplir le bon. Cependant, le symbole `errno` montré dans cet exemple est spécial dans la plupart des compilateurs, et donc la valeur vue ici n'est probablement pas ce que vous attendez ou souhaitez. Compiler le code équivalent en C sur n'importe quel système capable de multi-threading appellerait généralement en réalité une fonction différente (via la surcharge du préprocesseur macro), et peut donner un résultat différent de la valeur héritée imprimée ici.


## Accessing Data through a Pointer

Les méthodes suivantes sont décrites comme "non sécurisées" car un mauvais pointeur ou une déclaration de type incorrecte peuvent entraîner une terminaison abrupte de Julia.

Étant donné un `Ptr{T}`, le contenu de type `T` peut généralement être copié de la mémoire référencée dans un objet Julia en utilisant `unsafe_load(ptr, [index])`. L'argument index est optionnel (la valeur par défaut est 1) et suit la convention Julia d'indexation basée sur 1. Cette fonction est intentionnellement similaire au comportement de [`getindex`](@ref) et [`setindex!`](@ref) (par exemple, la syntaxe d'accès `[]`).

La valeur de retour sera un nouvel objet initialisé pour contenir une copie du contenu de la mémoire référencée. La mémoire référencée peut être libérée ou désallouée en toute sécurité.

Si `T` est `Any`, alors la mémoire est supposée contenir une référence à un objet Julia (un `jl_value_t*`), le résultat sera une référence à cet objet, et l'objet ne sera pas copié. Vous devez être prudent dans ce cas pour vous assurer que l'objet était toujours visible pour le ramasse-miettes (les pointeurs ne comptent pas, mais la nouvelle référence le fait) afin de garantir que la mémoire ne soit pas libérée prématurément. Notez que si l'objet n'a pas été initialement alloué par Julia, le nouvel objet ne sera jamais finalisé par le ramasse-miettes de Julia. Si le `Ptr` est en réalité un `jl_value_t*`, il peut être converti en référence d'objet Julia par [`unsafe_pointer_to_objref(ptr)`](@ref). (Les valeurs Julia `v` peuvent être converties en pointeurs `jl_value_t*`, en tant que `Ptr{Cvoid}`, en appelant [`pointer_from_objref(v)`](@ref).)

L'opération inverse (écriture de données dans un `Ptr{T}`) peut être effectuée en utilisant [`unsafe_store!(ptr, value, [index])`](@ref). Actuellement, cela n'est pris en charge que pour les types primitifs ou d'autres types de structures immuables sans pointeur (`isbits`).

Toute opération qui génère une erreur est probablement actuellement non implémentée et devrait être signalée comme un bug afin qu'elle puisse être résolue.

Si le pointeur d'intérêt est un tableau de données simples (type primitif ou structure immuable), la fonction [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref) peut être plus utile. Le dernier paramètre doit être vrai si Julia doit "prendre possession" du tampon sous-jacent et appeler `free(ptr)` lorsque l'objet `Array` retourné est finalisé. Si le paramètre `own` est omis ou faux, l'appelant doit s'assurer que le tampon reste en existence jusqu'à ce que tout l'accès soit complet.

L'arithmétique sur le type `Ptr` en Julia (par exemple, en utilisant `+`) ne se comporte pas de la même manière que l'arithmétique des pointeurs en C. Ajouter un entier à un `Ptr` en Julia déplace toujours le pointeur d'un certain nombre de *octets*, et non d'éléments. De cette manière, les valeurs d'adresse obtenues par l'arithmétique des pointeurs ne dépendent pas des types d'éléments des pointeurs.

## Thread-safety

Certaines bibliothèques C exécutent leurs rappels à partir d'un thread différent, et comme Julia n'est pas thread-safe, vous devrez prendre des précautions supplémentaires. En particulier, vous devrez mettre en place un système à deux niveaux : le rappel C ne doit que *planifier* (via la boucle d'événements de Julia) l'exécution de votre "vrai" rappel. Pour ce faire, créez un [`AsyncCondition`](@ref Base.AsyncCondition) objet et [`wait`](@ref) dessus :

```julia
cond = Base.AsyncCondition()
wait(cond)
```

Le rappel que vous passez à C ne doit exécuter qu'un [`ccall`](@ref) à `:uv_async_send`, en passant `cond.handle` comme argument, en veillant à éviter toute allocation ou autre interaction avec le runtime Julia.

Notez que les événements peuvent être fusionnés, donc plusieurs appels à `uv_async_send` peuvent entraîner une seule notification de réveil à la condition.

## More About Callbacks

Pour plus de détails sur la façon de passer des rappels aux bibliothèques C, consultez ce [blog post](https://julialang.org/blog/2013/05/callback).

## C++

Pour les outils de création de liaisons C++, consultez le package [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl).

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
