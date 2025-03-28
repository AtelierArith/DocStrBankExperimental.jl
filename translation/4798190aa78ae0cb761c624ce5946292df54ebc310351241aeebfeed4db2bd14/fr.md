```
ENV
```

Référence au singleton `EnvDict`, fournissant une interface de dictionnaire pour les variables d'environnement système.

(Sous Windows, les variables d'environnement système ne tiennent pas compte de la casse, et `ENV` convertit donc toutes les clés en majuscules pour l'affichage, l'itération et la copie. Le code portable ne doit pas s'appuyer sur la capacité à distinguer les variables par leur casse, et doit être conscient que définir une variable apparemment en minuscules peut entraîner une clé `ENV` en majuscules.)

!!! avertissement
    La mutation de l'environnement n'est pas thread-safe.


# Exemples

```julia-repl
julia> ENV
Base.EnvDict avec "50" entrées :
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "nom_utilisateur"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

Voir aussi : [`withenv`](@ref), [`addenv`](@ref).
