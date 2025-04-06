# Handling Operating System Variation

Al escribir aplicaciones o bibliotecas multiplataforma, a menudo es necesario permitir diferencias entre sistemas operativos. La variable `Sys.KERNEL` se puede utilizar para manejar tales casos. Hay varias funciones en el módulo `Sys` destinadas a facilitar esto, como `isunix`, `islinux`, `isapple`, `isbsd`, `isfreebsd` e `iswindows`. Estas se pueden usar de la siguiente manera:

```julia
if Sys.iswindows()
    windows_specific_thing(a)
end
```

Tenga en cuenta que `islinux`, `isapple` e `isfreebsd` son subconjuntos mutuamente excluyentes de `isunix`. Además, hay un macro `@static` que hace posible usar estas funciones para ocultar condicionalmente código inválido, como se demuestra en los siguientes ejemplos.

Bloques simples:

```
ccall((@static Sys.iswindows() ? :_fopen : :fopen), ...)
```

Bloques complejos:

```julia
@static if Sys.islinux()
    linux_specific_thing(a)
elseif Sys.isapple()
    apple_specific_thing(a)
else
    generic_thing(a)
end
```

Al anidar condicionales, el `@static` debe repetirse para cada nivel (los paréntesis son opcionales, pero se recomiendan para mejorar la legibilidad):

```julia
@static Sys.iswindows() ? :a : (@static Sys.isapple() ? :b : :c)
```
