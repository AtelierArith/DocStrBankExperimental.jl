```
show(io::IO, mime, x)
```

Les fonctions [`display`](@ref) appellent finalement `show` afin d'écrire un objet `x` sous un type `mime` donné dans un flux d'E/S `io` donné (généralement un tampon mémoire), si possible. Pour fournir une représentation multimédia riche d'un type défini par l'utilisateur `T`, il suffit de définir une nouvelle méthode `show` pour `T`, via : `show(io, ::MIME"mime", x::T) = ...`, où `mime` est une chaîne de caractères de type MIME et le corps de la fonction appelle [`write`](@ref) (ou similaire) pour écrire cette représentation de `x` dans `io`. (Notez que la notation `MIME""` ne prend en charge que des chaînes littérales ; pour construire des types `MIME` de manière plus flexible, utilisez `MIME{Symbol("")}`.)

Par exemple, si vous définissez un type `MyImage` et savez comment l'écrire dans un fichier PNG, vous pourriez définir une fonction `show(io, ::MIME"image/png", x::MyImage) = ...` pour permettre à vos images d'être affichées sur tout `AbstractDisplay` capable de PNG (comme IJulia). Comme d'habitude, assurez-vous d'`importer Base.show` afin d'ajouter de nouvelles méthodes à la fonction intégrée Julia `show`.

Techniquement, la macro `MIME"mime"` définit un type singleton pour la chaîne `mime` donnée, ce qui nous permet d'exploiter les mécanismes de dispatch de Julia pour déterminer comment afficher des objets de tout type donné.

Le type MIME par défaut est `MIME"text/plain"`. Il existe une définition de secours pour la sortie `text/plain` qui appelle `show` avec 2 arguments, donc il n'est pas toujours nécessaire d'ajouter une méthode pour ce cas. Si un type bénéficie d'une sortie personnalisée lisible par un humain, `show(::IO, ::MIME"text/plain", ::T)` devrait être défini. Par exemple, le type `Day` utilise `1 day` comme sortie pour le type MIME `text/plain`, et `Day(1)` comme sortie de `show` à 2 arguments.

# Exemples

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

Les types conteneurs implémentent généralement `show` à 3 arguments en appelant `show(io, MIME"text/plain"(), x)` pour les éléments `x`, avec `:compact => true` défini dans un [`IOContext`](@ref) passé comme premier argument.
