```
@ncall N f sym...
```

Generiere einen Funktionsaufruf-Ausdruck. `sym` steht für eine beliebige Anzahl von Funktionsargumenten, wobei das letzte eine anonyme Funktionsausdruck sein kann und in `N` Argumente erweitert wird.

Zum Beispiel erzeugt `@ncall 3 func a` 

```
func(a_1, a_2, a_3)
```

während `@ncall 2 func a b i->c[i]` 

```
func(a, b, c[1], c[2])
```

liefert.
