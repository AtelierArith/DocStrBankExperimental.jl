```
@static
```

Évalue partiellement une expression au moment de l'analyse.

Par exemple, `@static Sys.iswindows() ? foo : bar` évaluera `Sys.iswindows()` et insérera soit `foo` soit `bar` dans l'expression. Cela est utile dans les cas où une construction serait invalide sur d'autres plateformes, comme un `ccall` à une fonction inexistante. `@static if Sys.isapple() foo end` et `@static foo <&&,||> bar` sont également une syntaxe valide.
