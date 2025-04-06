```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

Écrivez `data` en syntaxe TOML dans le flux `io`. Si l'argument clé `sorted` est défini sur `true`, triez les tables selon la fonction donnée par l'argument clé `by`. Si l'argument clé `inline_tables` est donné, il doit s'agir d'un ensemble de tables qui doivent être imprimées "inline".

Les types de données suivants sont pris en charge : `AbstractDict`, `AbstractVector`, `AbstractString`, `Integer`, `AbstractFloat`, `Bool`, `Dates.DateTime`, `Dates.Time`, `Dates.Date`. Notez que les entiers et les flottants doivent être convertibles en `Float64` et `Int64` respectivement. Pour d'autres types de données, passez la fonction `to_toml` qui prend les types de données et renvoie une valeur d'un type pris en charge.
