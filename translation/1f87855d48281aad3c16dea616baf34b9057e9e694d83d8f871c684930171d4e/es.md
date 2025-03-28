```
IndexStyle(A)
IndexStyle(typeof(A))
```

`IndexStyle` especifica el "estilo de indexación nativo" para el arreglo `A`. Cuando defines un nuevo tipo de [`AbstractArray`](@ref), puedes elegir implementar ya sea indexación lineal (con [`IndexLinear`](@ref)) o indexación cartesiana. Si decides implementar solo la indexación lineal, entonces debes establecer este rasgo para tu tipo de arreglo:

```
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

El valor predeterminado es [`IndexCartesian()`](@ref).

La maquinaria de indexación interna de Julia recomputará automáticamente (e invisiblemente) todas las operaciones de indexación en el estilo preferido. Esto permite a los usuarios acceder a los elementos de tu arreglo utilizando cualquier estilo de indexación, incluso cuando no se han proporcionado métodos explícitos.

Si defines ambos estilos de indexación para tu `AbstractArray`, este rasgo puede ser utilizado para seleccionar el estilo de indexación más eficiente. Algunos métodos verifican este rasgo en sus entradas y despachan a diferentes algoritmos dependiendo del patrón de acceso más eficiente. En particular, [`eachindex`](@ref) crea un iterador cuyo tipo depende de la configuración de este rasgo.
