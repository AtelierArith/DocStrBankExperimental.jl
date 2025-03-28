```
StridedArray{T, N}
```

Un [`Union`](@ref) codificado de tipos de arreglo comunes que siguen la [interfaz de arreglo estratificado](@ref man-interface-strided-arrays), con elementos de tipo `T` y `N` dimensiones.

Si `A` es un `StridedArray`, entonces sus elementos se almacenan en memoria con desplazamientos, que pueden variar entre dimensiones pero son constantes dentro de una dimensión. Por ejemplo, `A` podría tener un desplazamiento de 2 en la dimensión 1, y un desplazamiento de 3 en la dimensión 2. Incrementar `A` a lo largo de la dimensión `d` salta en memoria por [`stride(A, d)`] espacios. Los arreglos estratificados son particularmente importantes y útiles porque a veces pueden ser pasados directamente como punteros a bibliotecas de lenguajes extranjeros como BLAS.
