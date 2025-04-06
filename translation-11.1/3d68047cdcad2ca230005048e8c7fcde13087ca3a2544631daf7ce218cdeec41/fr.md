```
ReentrantLock()
```

Crée un verrou réentrant pour synchroniser les [`Task`](@ref)s. La même tâche peut acquérir le verrou autant de fois que nécessaire (c'est ce que signifie la partie "Réentrant" du nom). Chaque [`lock`](@ref) doit être associé à un [`unlock`](@ref).

Appeler `lock` inhibera également l'exécution des finaliseurs sur ce thread jusqu'au `unlock` correspondant. L'utilisation du modèle de verrouillage standard illustré ci-dessous devrait être naturellement supportée, mais attention à inverser l'ordre try/lock ou à manquer complètement le bloc try (par exemple, tenter de retourner avec le verrou toujours détenu) :

Cela fournit un ordre de mémoire d'acquisition/libération sur les appels lock/unlock.

```
lock(l)
try
    <travail atomique>
finally
    unlock(l)
end
```

Si [`!islocked(lck::ReentrantLock)`](@ref islocked) est vrai, [`trylock(lck)`](@ref trylock) réussit à moins qu'il y ait d'autres tâches tentant de détenir le verrou "en même temps."
