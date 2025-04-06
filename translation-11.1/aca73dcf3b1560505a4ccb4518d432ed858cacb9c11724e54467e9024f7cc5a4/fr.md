```
unsafe_pointer_to_objref(p::Ptr)
```

Convertit un `Ptr` en une référence d'objet. Supposons que le pointeur fasse référence à un objet Julia valide alloué sur le tas. Si ce n'est pas le cas, un comportement indéfini en résulte, c'est pourquoi cette fonction est considérée comme "dangereuse" et doit être utilisée avec précaution.

Voir aussi [`pointer_from_objref`](@ref).
