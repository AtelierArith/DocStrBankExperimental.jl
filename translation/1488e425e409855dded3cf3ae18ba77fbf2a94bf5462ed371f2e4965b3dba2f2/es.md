```
@ncall N f sym...
```

Genera una expresión de llamada a función. `sym` representa cualquier número de argumentos de función, el último de los cuales puede ser una expresión de función anónima y se expande en `N` argumentos.

Por ejemplo, `@ncall 3 func a` genera

```
func(a_1, a_2, a_3)
```

mientras que `@ncall 2 func a b i->c[i]` produce

```
func(a, b, c[1], c[2])
```
