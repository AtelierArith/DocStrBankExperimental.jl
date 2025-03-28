```
let
```

Les blocs `let` créent un nouveau scope strict et introduisent éventuellement de nouvelles liaisons locales.

Tout comme les [autres constructions de scope](@ref man-scope-table), les blocs `let` définissent le bloc de code où les nouvelles variables locales introduites sont accessibles. De plus, la syntaxe a une signification spéciale pour les affectations séparées par des virgules et les noms de variables qui peuvent éventuellement apparaître sur la même ligne que le `let` :

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

Les variables introduites sur cette ligne sont locales au bloc `let` et les affectations sont évaluées dans l'ordre, chaque côté droit étant évalué dans le scope sans tenir compte du nom à gauche. Il est donc logique d'écrire quelque chose comme `let x = x`, puisque les deux variables `x` sont distinctes avec le côté gauche masquant localement le `x` du scope extérieur. Cela peut même être un idiome utile car de nouvelles variables locales sont fraîchement créées chaque fois que des scopes locaux sont entrés, mais cela n'est observable que dans le cas de variables qui survivent à leur scope via des fermetures. Une variable `let` sans affectation, comme `var2` dans l'exemple ci-dessus, déclare une nouvelle variable locale qui n'est pas encore liée à une valeur.

En revanche, les blocs [`begin`](@ref) regroupent également plusieurs expressions ensemble mais n'introduisent pas de scope ni n'ont la syntaxe d'affectation spéciale.

### Exemples

Dans la fonction ci-dessous, il y a un seul `x` qui est mis à jour de manière itérative trois fois par le `map`. Les fermetures retournées font toutes référence à ce `x` à sa valeur finale :

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generic function with 1 method)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

Cependant, si nous ajoutons un bloc `let` qui introduit une nouvelle variable locale, nous nous retrouverons avec trois variables distinctes capturées (une à chaque itération) même si nous avons choisi d'utiliser (masquer) le même nom.

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generic function with 1 method)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

Toutes les constructions de scope qui introduisent de nouvelles variables locales se comportent de cette manière lorsqu'elles sont exécutées plusieurs fois ; la caractéristique distinctive de `let` est sa capacité à déclarer succinctement de nouveaux `local`s qui peuvent masquer des variables extérieures du même nom. Par exemple, utiliser directement l'argument de la fonction `do` capture également trois variables distinctes :

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generic function with 1 method)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```
