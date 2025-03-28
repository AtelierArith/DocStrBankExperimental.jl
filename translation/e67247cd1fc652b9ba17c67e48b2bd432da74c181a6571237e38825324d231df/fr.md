```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

Enregistre un message dans `logger` au niveau `level`. L'emplacement logique où le message a été généré est donné par le module `_module` et le groupe ; l'emplacement source par `file` et `line`. `id` est une valeur unique arbitraire (typiquement un [`Symbol`](@ref)) à utiliser comme clé pour identifier l'instruction de journalisation lors du filtrage.
