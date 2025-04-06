```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

Genera `N` bucles anidados, utilizando `itersym` como el prefijo para las variables de iteración. `rangeexpr` puede ser una expresión de función anónima, o un símbolo simple `var`, en cuyo caso el rango es `axes(var, d)` para la dimensión `d`.

Opcionalmente, puedes proporcionar expresiones "pre" y "post". Estas se ejecutan primero y al final, respectivamente, en el cuerpo de cada bucle. Por ejemplo:

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

generaría:

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

Si solo deseas una expresión post, proporciona [`nothing`](@ref) para la expresión pre. Usando paréntesis y punto y coma, puedes proporcionar expresiones de múltiples declaraciones.
