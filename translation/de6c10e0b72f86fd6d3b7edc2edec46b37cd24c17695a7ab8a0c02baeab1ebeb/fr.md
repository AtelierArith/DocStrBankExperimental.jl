```
write(io::IO, x)
```

Écrivez la représentation binaire canonique d'une valeur dans le flux ou le fichier I/O donné. Retournez le nombre d'octets écrits dans le flux. Voir aussi [`print`](@ref) pour écrire une représentation textuelle (avec un encodage qui peut dépendre de `io`).

L'endianness de la valeur écrite dépend de l'endianness du système hôte. Convertissez vers/depuis une endianness fixe lors de l'écriture/de la lecture (par exemple, en utilisant [`htol`](@ref) et [`ltoh`](@ref)) pour obtenir des résultats cohérents sur différentes plateformes.

Vous pouvez écrire plusieurs valeurs avec le même appel à `write`. c'est-à-dire que les éléments suivants sont équivalents :

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# Exemples

Sérialisation cohérente :

```jldoctest
julia> fname = tempname(); # nom de fichier temporaire aléatoire

julia> open(fname,"w") do f
           # Assurez-vous d'écrire un entier 64 bits dans l'ordre des octets little-endian
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # Convertir à nouveau en ordre des octets hôte et type d'entier hôte
           Int(ltoh(read(f,Int64)))
       end
42
```

Fusion des appels d'écriture :

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang est une organisation GitHub.", " Elle a de nombreux membres.")
56

julia> String(take!(io))
"JuliaLang est une organisation GitHub. Elle a de nombreux membres."

julia> write(io, "Parfois ces membres") + write(io, " écrivent de la documentation.")
44

julia> String(take!(io))
"Parfois ces membres écrivent de la documentation."
```

Les types de données simples définis par l'utilisateur sans méthodes `write` peuvent être écrits lorsqu'ils sont enveloppés dans un `Ref` :

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
