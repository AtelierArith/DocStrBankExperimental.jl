```
codepoint(c::AbstractChar) -> Integer
```

Devuelve el punto de código Unicode (un entero sin signo) correspondiente al carácter `c` (o lanza una excepción si `c` no representa un carácter válido). Para `Char`, este es un valor `UInt32`, pero los tipos `AbstractChar` que representan solo un subconjunto de Unicode pueden devolver un entero de diferente tamaño (por ejemplo, `UInt8`).
