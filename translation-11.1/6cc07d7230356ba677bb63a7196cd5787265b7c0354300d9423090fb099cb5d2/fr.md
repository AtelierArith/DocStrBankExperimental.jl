```
unsafe_convert(T, x)
```

Convertir `x` en un argument C de type `T` où l'entrée `x` doit être la valeur de retour de `cconvert(T, ...)`.

Dans les cas où [`convert`](@ref) devrait prendre un objet Julia et le transformer en un `Ptr`, cette fonction doit être utilisée pour définir et effectuer cette conversion.

Soyez prudent pour vous assurer qu'une référence Julia à `x` existe tant que le résultat de cette fonction sera utilisé. En conséquence, l'argument `x` de cette fonction ne doit jamais être une expression, seulement un nom de variable ou une référence de champ. Par exemple, `x=a.b.c` est acceptable, mais `x=[a,b,c]` ne l'est pas.

Le préfixe `unsafe` sur cette fonction indique que l'utilisation du résultat de cette fonction après que l'argument `x` de cette fonction ne soit plus accessible au programme peut entraîner un comportement indéfini, y compris la corruption du programme ou des segfaults, à tout moment ultérieur.

Voir aussi [`cconvert`](@ref)
