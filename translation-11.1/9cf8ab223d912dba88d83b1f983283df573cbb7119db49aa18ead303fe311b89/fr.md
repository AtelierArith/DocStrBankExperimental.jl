```
@test_logs [log_patterns...] [keywords] expression
```

Collectez une liste d'enregistrements de journal générés par `expression` en utilisant `collect_test_logs`, vérifiez qu'ils correspondent à la séquence `log_patterns`, et renvoyez la valeur de `expression`. Les `keywords` fournissent un filtrage simple des enregistrements de journal : le mot-clé `min_level` contrôle le niveau de journal minimum qui sera collecté pour le test, le mot-clé `match_mode` définit comment la correspondance sera effectuée (le `:all` par défaut vérifie que tous les journaux et motifs correspondent par paires ; utilisez `:any` pour vérifier que le motif correspond au moins une fois quelque part dans la séquence.)

Le motif de journal le plus utile est un simple tuple de la forme `(level,message)`. Un nombre différent d'éléments de tuple peut être utilisé pour correspondre à d'autres métadonnées de journal, correspondant aux arguments passés à `AbstractLogger` via la fonction `handle_message` : `(level,message,module,group,id,file,line)`. Les éléments qui sont présents seront appariés par paires avec les champs d'enregistrement de journal en utilisant `==` par défaut, avec les cas spéciaux que les `Symbol`s peuvent être utilisés pour les niveaux de journal standard, et les `Regex`s dans le motif correspondront aux champs de chaîne ou de symbole en utilisant `occursin`.

# Exemples

Considérez une fonction qui enregistre un avertissement et plusieurs messages de débogage :

```
function foo(n)
    @info "Doing foo with n=$n"
    for i=1:n
        @debug "Iteration $i"
    end
    42
end
```

Nous pouvons tester le message d'information en utilisant

```
@test_logs (:info,"Doing foo with n=2") foo(2)
```

Si nous voulons également tester les messages de débogage, ceux-ci doivent être activés avec le mot-clé `min_level` :

```
using Logging
@test_logs (:info,"Doing foo with n=2") (:debug,"Iteration 1") (:debug,"Iteration 2") min_level=Logging.Debug foo(2)
```

Si vous souhaitez tester que certains messages particuliers sont générés tout en ignorant le reste, vous pouvez définir le mot-clé `match_mode=:any` :

```
using Logging
@test_logs (:info,) (:debug,"Iteration 42") min_level=Logging.Debug match_mode=:any foo(100)
```

Le macro peut être enchaîné avec `@test` pour tester également la valeur renvoyée :

```
@test (@test_logs (:info,"Doing foo with n=2") foo(2)) == 42
```

Si vous souhaitez tester l'absence d'avertissements, vous pouvez omettre la spécification des motifs de journal et définir le `min_level` en conséquence :

```
# test que l'expression ne journalise aucun message lorsque le niveau du journal est averti :
@test_logs min_level=Logging.Warn @info("Some information") # passe
@test_logs min_level=Logging.Warn @warn("Some information") # échoue
```

Si vous souhaitez tester l'absence d'avertissements (ou de messages d'erreur) dans [`stderr`](@ref) qui ne sont pas générés par `@warn`, consultez [`@test_nowarn`](@ref).
