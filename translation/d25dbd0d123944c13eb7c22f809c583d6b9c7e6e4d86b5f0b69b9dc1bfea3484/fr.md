```
@everywhere [procs()] expr
```

Exécute une expression sous `Main` sur tous les `procs`. Les erreurs sur l'un des processus sont collectées dans une [`CompositeException`](@ref) et lancées. Par exemple :

```
@everywhere bar = 1
```

définira `Main.bar` sur tous les processus actuels. Les processus ajoutés plus tard (par exemple avec [`addprocs()`](@ref)) n'auront pas l'expression définie.

Contrairement à [`@spawnat`](@ref), `@everywhere` ne capture aucune variable locale. Au lieu de cela, les variables locales peuvent être diffusées en utilisant l'interpolation :

```
foo = 1
@everywhere bar = $foo
```

L'argument optionnel `procs` permet de spécifier un sous-ensemble de tous les processus pour exécuter l'expression.

Semblable à l'appel de `remotecall_eval(Main, procs, expr)`, mais avec deux fonctionnalités supplémentaires :

```
- Les instructions `using` et `import` s'exécutent d'abord sur le processus appelant, pour s'assurer que
  les paquets sont précompilés.
- Le chemin du fichier source actuel utilisé par `include` est propagé aux autres processus.
```
