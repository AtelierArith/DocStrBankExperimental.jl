```
IOContext(io::IO, KV::Pair...)
```

Crée un `IOContext` qui enveloppe un flux donné, ajoutant les paires `key=>value` spécifiées aux propriétés de ce flux (notez que `io` peut lui-même être un `IOContext`).

  * utilisez `(key => value) in io` pour voir si cette combinaison particulière est dans l'ensemble des propriétés
  * utilisez `get(io, key, default)` pour récupérer la valeur la plus récente pour une clé particulière

Les propriétés suivantes sont couramment utilisées :

  * `:compact` : Booléen spécifiant que les valeurs doivent être imprimées de manière plus compacte, par exemple que les nombres doivent être imprimés avec moins de chiffres. Cela est défini lors de l'impression des éléments d'un tableau. La sortie `:compact` ne doit pas contenir de sauts de ligne.
  * `:limit` : Booléen spécifiant que les conteneurs doivent être tronqués, par exemple en montrant `…` à la place de la plupart des éléments.
  * `:displaysize` : Un `Tuple{Int,Int}` donnant la taille en lignes et colonnes à utiliser pour la sortie texte. Cela peut être utilisé pour remplacer la taille d'affichage pour les fonctions appelées, mais pour obtenir la taille de l'écran, utilisez la fonction `displaysize`.
  * `:typeinfo` : un `Type` caractérisant les informations déjà imprimées concernant le type de l'objet sur le point d'être affiché. Cela est principalement utile lors de l'affichage d'une collection d'objets du même type, afin d'éviter les informations de type redondantes (par exemple, `[Float16(0)]` peut être affiché comme "Float16[0.0]" au lieu de "Float16[Float16(0.0)]" : lors de l'affichage des éléments du tableau, la propriété `:typeinfo` sera définie sur `Float16`).
  * `:color` : Booléen spécifiant si les codes de couleur/évasion ANSI sont pris en charge/attendus. Par défaut, cela est déterminé par le fait que `io` soit un terminal compatible et par tout drapeau de ligne de commande `--color` lorsque `julia` a été lancé.

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generic function with 1 method)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```
