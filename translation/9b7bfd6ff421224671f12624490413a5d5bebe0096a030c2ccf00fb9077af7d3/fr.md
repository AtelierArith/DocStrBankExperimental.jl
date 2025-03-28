```
macro
```

`macro` définit une méthode pour insérer du code généré dans un programme. Un macro associe une séquence d'expressions d'arguments à une expression retournée, et l'expression résultante est substituée directement dans le programme au point où le macro est invoqué. Les macros sont un moyen d'exécuter du code généré sans appeler [`eval`](@ref Main.eval), puisque le code généré devient simplement une partie du programme environnant. Les arguments des macros peuvent inclure des expressions, des valeurs littérales et des symboles. Les macros peuvent être définies pour un nombre variable d'arguments (varargs), mais n'acceptent pas d'arguments de mot-clé. Chaque macro reçoit également implicitement les arguments `__source__`, qui contient le numéro de ligne et le nom de fichier d'où le macro est appelé, et `__module__`, qui est le module dans lequel le macro est développé.

Voir la section du manuel sur [Metaprogramming](@ref) pour plus d'informations sur la façon d'écrire un macro.

# Exemples

```jldoctest
julia> macro sayhello(name)
           return :( println("Hello, ", $name, "!") )
       end
@sayhello (macro with 1 method)

julia> @sayhello "Charlie"
Hello, Charlie!

julia> macro saylots(x...)
           return :( println("Say: ", $(x...)) )
       end
@saylots (macro with 1 method)

julia> @saylots "hey " "there " "friend"
Say: hey there friend
```
