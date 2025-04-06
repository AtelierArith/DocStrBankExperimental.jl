```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

Konstruiere einen `GenericMemoryRef` aus einem Speicherobjekt und einem Offset-Index (1-basiert), der auch negativ sein kann. Dies gibt immer ein gültiges Objekt zurück und wirft einen Fehler, wenn dies nicht möglich ist (weil der Index zu einer Verschiebung außerhalb der Grenzen des zugrunde liegenden Speichers führen würde).
