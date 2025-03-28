```
cconvert(T,x)
```

Convierte `x` a un valor que se pasará al código C como tipo `T`, típicamente llamando a `convert(T, x)`.

En los casos donde `x` no puede ser convertido de manera segura a `T`, a diferencia de [`convert`](@ref), `cconvert` puede devolver un objeto de un tipo diferente a `T`, que sin embargo es adecuado para que [`unsafe_convert`](@ref) lo maneje. El resultado de esta función debe mantenerse válido (para el GC) hasta que el resultado de [`unsafe_convert`](@ref) ya no sea necesario. Esto se puede usar para asignar memoria que será accedida por el `ccall`. Si se necesitan asignar múltiples objetos, se puede usar una tupla de los objetos como valor de retorno.

Ni `convert` ni `cconvert` deben tomar un objeto de Julia y convertirlo en un `Ptr`.
