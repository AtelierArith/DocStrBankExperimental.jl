```
@ncall N f sym...
```

Générez une expression d'appel de fonction. `sym` représente un nombre quelconque d'arguments de fonction, dont le dernier peut être une expression de fonction anonyme et est développé en `N` arguments.

Par exemple, `@ncall 3 func a` génère

```
func(a_1, a_2, a_3)
```

tandis que `@ncall 2 func a b i->c[i]` produit

```
func(a, b, c[1], c[2])
```
