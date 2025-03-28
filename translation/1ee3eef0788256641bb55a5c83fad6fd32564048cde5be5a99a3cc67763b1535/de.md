```
StridedArray{T, N}
```

Ein fest codierter [`Union`](@ref) gängiger Array-Typen, die der [strided array interface](@ref man-interface-strided-arrays) folgen, mit Elementen vom Typ `T` und `N` Dimensionen.

Wenn `A` ein `StridedArray` ist, dann werden seine Elemente im Speicher mit Offsets gespeichert, die zwischen den Dimensionen variieren können, aber innerhalb einer Dimension konstant sind. Zum Beispiel könnte `A` in Dimension 1 einen Stride von 2 und in Dimension 2 einen Stride von 3 haben. Das Inkrementieren von `A` entlang der Dimension `d` springt im Speicher um [`stride(A, d)`] Slots. Strided Arrays sind besonders wichtig und nützlich, da sie manchmal direkt als Zeiger an Bibliotheken fremder Sprachen wie BLAS übergeben werden können.
