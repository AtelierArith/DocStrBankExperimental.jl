```
const
```

`const` se utiliza para declarar variables globales cuyos valores no cambiarán. En casi todo el código (y particularmente en el código sensible al rendimiento), las variables globales deben declararse constantes de esta manera.

```julia
const x = 5
```

Se pueden declarar múltiples variables dentro de un solo `const`:

```julia
const y, z = 7, 11
```

Ten en cuenta que `const` solo se aplica a una operación de `=`; por lo tanto, `const x = y = 1` declara `x` como constante pero no `y`. Por otro lado, `const x = const y = 1` declara tanto `x` como `y` constantes.

Ten en cuenta que la "constancia" no se extiende a contenedores mutables; solo la asociación entre una variable y su valor es constante. Si `x` es un arreglo o un diccionario (por ejemplo), aún puedes modificar, agregar o eliminar elementos.

En algunos casos, cambiar el valor de una variable `const` da una advertencia en lugar de un error. Sin embargo, esto puede producir un comportamiento impredecible o corromper el estado de tu programa, por lo que debe evitarse. Esta característica está destinada solo para conveniencia durante el uso interactivo.
