```
transcode(T, src)
```

Convertir des données de chaîne entre les encodages Unicode. `src` est soit une `String` soit un `Vector{UIntXX}` d'unités de code UTF-XX, où `XX` est 8, 16 ou 32. `T` indique l'encodage de la valeur de retour : `String` pour retourner une `String` (encodée en UTF-8) ou `UIntXX` pour retourner un `Vector{UIntXX}` de données UTF-`XX`. (L'alias [`Cwchar_t`](@ref) peut également être utilisé comme type entier, pour convertir des chaînes `wchar_t*` utilisées par des bibliothèques C externes.)

La fonction `transcode` réussit tant que les données d'entrée peuvent être raisonnablement représentées dans l'encodage cible ; elle réussit toujours pour les conversions entre les encodages UTF-XX, même pour des données Unicode invalides.

Seule la conversion vers/depuis UTF-8 est actuellement prise en charge.

# Exemples

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
