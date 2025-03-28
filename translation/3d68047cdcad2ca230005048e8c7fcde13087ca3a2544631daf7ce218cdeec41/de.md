```
ReentrantLock()
```

Erstellt ein re-entrantes Schloss zur Synchronisierung von [`Task`](@ref)s. Derselbe Task kann das Schloss so oft erwerben, wie erforderlich (das ist es, was der "Reentrant"-Teil des Namens bedeutet). Jedes [`lock`](@ref) muss mit einem [`unlock`](@ref) übereinstimmen.

Der Aufruf von `lock` wird auch die Ausführung von Finalisierern in diesem Thread bis zum entsprechenden `unlock` verhindern. Die Verwendung des standardmäßigen Schlossmusters, das unten veranschaulicht wird, sollte natürlich unterstützt werden, aber seien Sie vorsichtig, die Reihenfolge von try/lock umzukehren oder den try-Block ganz zu verpassen (z. B. zu versuchen, zurückzukehren, während das Schloss noch gehalten wird):

Dies bietet eine Erwerb/Freigabe-Speicherreihenfolge bei lock/unlock-Aufrufen.

```
lock(l)
try
    <atomare Arbeit>
finally
    unlock(l)
end
```

Wenn [`!islocked(lck::ReentrantLock)`](@ref islocked) gilt, gelingt [`trylock(lck)`](@ref trylock), es sei denn, es gibt andere Tasks, die versuchen, das Schloss "zur gleichen Zeit" zu halten.
