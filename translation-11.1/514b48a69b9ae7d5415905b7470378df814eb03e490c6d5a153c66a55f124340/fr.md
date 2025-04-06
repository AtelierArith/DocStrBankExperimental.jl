```
cconvert(T,x)
```

Convertir `x` en une valeur à passer au code C en tant que type `T`, généralement en appelant `convert(T, x)`.

Dans les cas où `x` ne peut pas être converti en toute sécurité en `T`, contrairement à [`convert`](@ref), `cconvert` peut renvoyer un objet d'un type différent de `T`, qui est cependant adapté pour que [`unsafe_convert`](@ref) puisse le gérer. Le résultat de cette fonction doit rester valide (pour le GC) jusqu'à ce que le résultat de [`unsafe_convert`](@ref) ne soit plus nécessaire. Cela peut être utilisé pour allouer de la mémoire qui sera accessible par le `ccall`. Si plusieurs objets doivent être alloués, un tuple des objets peut être utilisé comme valeur de retour.

Ni `convert` ni `cconvert` ne devraient prendre un objet Julia et le transformer en un `Ptr`.
