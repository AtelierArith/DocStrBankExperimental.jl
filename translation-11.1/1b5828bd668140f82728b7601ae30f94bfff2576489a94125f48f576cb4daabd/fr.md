# Handling Operating System Variation

Lors de l'écriture d'applications ou de bibliothèques multiplateformes, il est souvent nécessaire de tenir compte des différences entre les systèmes d'exploitation. La variable `Sys.KERNEL` peut être utilisée pour gérer de tels cas. Il existe plusieurs fonctions dans le module `Sys` destinées à faciliter cela, telles que `isunix`, `islinux`, `isapple`, `isbsd`, `isfreebsd` et `iswindows`. Celles-ci peuvent être utilisées comme suit :

```julia
if Sys.iswindows()
    windows_specific_thing(a)
end
```

Notez que `islinux`, `isapple` et `isfreebsd` sont des sous-ensembles mutuellement exclusifs de `isunix`. De plus, il existe un macro `@static` qui permet d'utiliser ces fonctions pour masquer conditionnellement du code invalide, comme démontré dans les exemples suivants.

Blocs simples :

```
ccall((@static Sys.iswindows() ? :_fopen : :fopen), ...)
```

Blocs complexes :

```julia
@static if Sys.islinux()
    linux_specific_thing(a)
elseif Sys.isapple()
    apple_specific_thing(a)
else
    generic_thing(a)
end
```

Lorsqu'on imbrique des conditionnelles, le `@static` doit être répété pour chaque niveau (les parenthèses sont optionnelles, mais recommandées pour la lisibilité) :

```julia
@static Sys.iswindows() ? :a : (@static Sys.isapple() ? :b : :c)
```
