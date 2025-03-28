```
graphemes(s::AbstractString) -> GraphemeIterator
```

Devuelve un iterador sobre las subcadenas de `s` que corresponden a los grafemas extendidos en la cadena, tal como se define en Unicode UAX #29. (A grandes rasgos, estos son lo que los usuarios percibirían como caracteres individuales, aunque puedan contener más de un punto de código; por ejemplo, una letra combinada con un acento es un solo grafema.)
