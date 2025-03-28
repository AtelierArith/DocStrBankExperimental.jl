```
issuccess(F::LU; allowsingular = false)
```

Überprüfen Sie, ob die LU-Zerlegung einer Matrix erfolgreich war. Standardmäßig wird eine Zerlegung, die einen gültigen, aber rangdefizienten U-Faktor produziert, als Fehlschlag betrachtet. Dies kann geändert werden, indem `allowsingular = true` übergeben wird.

!!! compat "Julia 1.11"
    Das Schlüsselwortargument `allowsingular` wurde in Julia 1.11 hinzugefügt.


# Beispiele

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
