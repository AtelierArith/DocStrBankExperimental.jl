```
mmap(io::Union{IOStream,AbstractString,Mmap.AnonymousMmap}[, type::Type{Array{T,N}}, dims, offset]; grow::Bool=true, shared::Bool=true)
mmap(type::Type{Array{T,N}}, dims)
```

Créez un `Array` dont les valeurs sont liées à un fichier, en utilisant le mappage mémoire. Cela fournit un moyen pratique de travailler avec des données trop volumineuses pour tenir dans la mémoire de l'ordinateur.

Le type est un `Array{T,N}` avec un élément de type bits `T` et une dimension `N` qui détermine comment les octets du tableau sont interprétés. Notez que le fichier doit être stocké au format binaire, et aucune conversion de format n'est possible (c'est une limitation des systèmes d'exploitation, pas de Julia).

`dims` est un tuple ou un seul [`Integer`](@ref) spécifiant la taille ou la longueur du tableau.

Le fichier est passé via l'argument de flux, soit en tant que [`IOStream`](@ref) ouvert, soit en tant que chaîne de nom de fichier. Lorsque vous initialisez le flux, utilisez `"r"` pour un tableau "en lecture seule", et `"w+"` pour créer un nouveau tableau utilisé pour écrire des valeurs sur le disque.

Si aucun argument `type` n'est spécifié, la valeur par défaut est `Vector{UInt8}`.

En option, vous pouvez spécifier un décalage (en octets) si, par exemple, vous souhaitez ignorer un en-tête dans le fichier. La valeur par défaut pour le décalage est la position actuelle du flux pour un `IOStream`.

L'argument clé `grow` spécifie si le fichier disque doit être agrandi pour accueillir la taille demandée du tableau (si la taille totale du fichier est < taille de tableau demandée). Des privilèges d'écriture sont nécessaires pour agrandir le fichier.

L'argument clé `shared` spécifie si le `Array` résultant et les modifications qui y sont apportées seront visibles par d'autres processus mappant le même fichier.

Par exemple, le code suivant

```julia
# Créez un fichier pour le mmapping
# (vous pourriez également utiliser mmap pour faire cette étape, aussi)
using Mmap
A = rand(1:20, 5, 30)
s = open("/tmp/mmap.bin", "w+")
# Nous allons écrire les dimensions du tableau comme les deux premiers Ints dans le fichier
write(s, size(A,1))
write(s, size(A,2))
# Maintenant, écrivons les données
write(s, A)
close(s)

# Testez en le lisant à nouveau
s = open("/tmp/mmap.bin")   # la valeur par défaut est en lecture seule
m = read(s, Int)
n = read(s, Int)
A2 = mmap(s, Matrix{Int}, (m,n))
```

crée un `m`-par-`n` `Matrix{Int}`, lié au fichier associé au flux `s`.

Un fichier plus portable devrait encoder la taille des mots – 32 bits ou 64 bits – et les informations d'endianness dans l'en-tête. En pratique, envisagez d'encoder des données binaires en utilisant des formats standard comme HDF5 (qui peuvent être utilisés avec le mappage mémoire).
