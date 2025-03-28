```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

Écrit l'option à l'index `idx` dans `buf`. `iscursor`, s'il est `true`, indique que cet élément est à la position actuelle du curseur (celui qui sera sélectionné en appuyant sur "Entrée").

Si `m` est un `ConfiguredMenu`, `TerminalMenus` affichera l'indicateur de curseur. Sinon, l'appelant est censé gérer cette impression.

!!! compat "Julia 1.6"
    `writeline` nécessite Julia 1.6 ou supérieur.

    Dans les versions plus anciennes de Julia, c'était `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)` et `m` est supposé être non configuré. Les indicateurs de sélection et de curseur peuvent être obtenus à partir de `TerminalMenus.CONFIG`.

    Cette ancienne fonction est prise en charge sur toutes les versions Julia 1.x mais sera supprimée dans Julia 2.0.

