```
WeakKeyDict([itr])
```

`WeakKeyDict()` konstruiert eine Hashtabelle, in der die Schlüssel schwache Referenzen auf Objekte sind, die möglicherweise garbage collected werden, selbst wenn sie in einer Hashtabelle referenziert werden.

Siehe [`Dict`](@ref) für weitere Hilfe. Beachten Sie, dass `WeakKeyDict` im Gegensatz zu [`Dict`](@ref) die Schlüssel bei der Einfügung nicht konvertiert, da dies implizieren würde, dass das Schlüsselobjekt zuvor nirgendwo referenziert wurde.

Siehe auch [`WeakRef`](@ref).
