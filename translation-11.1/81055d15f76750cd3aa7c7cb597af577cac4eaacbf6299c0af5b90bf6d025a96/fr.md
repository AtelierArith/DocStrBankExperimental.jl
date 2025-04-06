```
init(; n::Integer, delay::Real)
```

Configurez le `delay` entre les backtraces (mesuré en secondes), et le nombre `n` de pointeurs d'instruction qui peuvent être stockés par thread. Chaque pointeur d'instruction correspond à une seule ligne de code ; les backtraces consistent généralement en une longue liste de pointeurs d'instruction. Notez que 6 espaces pour les pointeurs d'instruction par backtrace sont utilisés pour stocker des métadonnées et deux marqueurs de fin NULL. Les paramètres actuels peuvent être obtenus en appelant cette fonction sans arguments, et chacun peut être défini indépendamment en utilisant des mots-clés ou dans l'ordre `(n, delay)`.
