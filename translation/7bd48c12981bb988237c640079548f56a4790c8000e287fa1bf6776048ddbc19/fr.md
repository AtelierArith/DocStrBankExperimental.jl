```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

Générer `N` boucles imbriquées, en utilisant `itersym` comme préfixe pour les variables d'itération. `rangeexpr` peut être une expression de fonction anonyme, ou un symbole simple `var` dans ce cas la plage est `axes(var, d)` pour la dimension `d`.

En option, vous pouvez fournir des expressions "pré" et "post". Celles-ci sont exécutées en premier et en dernier, respectivement, dans le corps de chaque boucle. Par exemple :

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

générerait :

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

Si vous souhaitez juste une expression post, fournissez [`nothing`](@ref) pour l'expression pré. En utilisant des parenthèses et des points-virgules, vous pouvez fournir des expressions à plusieurs instructions.
