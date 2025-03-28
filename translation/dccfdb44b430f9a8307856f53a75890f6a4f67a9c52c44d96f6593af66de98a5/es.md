```
ImmutableDict
```

`ImmutableDict` es un diccionario implementado como una lista enlazada inmutable, que es óptima para diccionarios pequeños que se construyen a través de muchas inserciones individuales. Tenga en cuenta que no es posible eliminar un valor, aunque se puede sobrescribir parcialmente y ocultar insertando un nuevo valor con la misma clave.

```
ImmutableDict(KV::Pair)
```

Crea una nueva entrada en el `ImmutableDict` para un par `clave => valor`

  * use `(clave => valor) in dict` para ver si esta combinación particular está en el conjunto de propiedades
  * use `get(dict, clave, por_defecto)` para recuperar el valor más reciente para una clave particular
