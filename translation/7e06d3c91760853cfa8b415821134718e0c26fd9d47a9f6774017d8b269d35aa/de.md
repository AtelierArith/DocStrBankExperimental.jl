```
merge(a::NamedTuple, bs::NamedTuple...)
```

Konstruiere ein neues benanntes Tupel, indem zwei oder mehr vorhandene in einer linksassoziativen Weise zusammengeführt werden. Das Zusammenführen erfolgt von links nach rechts, zwischen Paaren von benannten Tupeln, und daher nehmen die Reihenfolge der Felder, die sowohl im links- als auch im rechtsseitigen benannten Tupel vorhanden sind, die gleiche Position ein, wie sie im linksseitigen benannten Tupel gefunden werden. Werte werden jedoch aus übereinstimmenden Feldern im rechtsseitigen benannten Tupel entnommen, das dieses Feld enthält. Felder, die nur im rechtsseitigen benannten Tupel eines Paares vorhanden sind, werden am Ende angehängt. Eine Rückfalloption wird implementiert, wenn nur ein einzelnes benanntes Tupel bereitgestellt wird, mit der Signatur `merge(a::NamedTuple)`.

!!! compat "Julia 1.1"
    Das Zusammenführen von 3 oder mehr `NamedTuple` erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> merge((a=1, b=2, c=3), (b=4, d=5))
(a = 1, b = 4, c = 3, d = 5)
```

```jldoctest
julia> merge((a=1, b=2), (b=3, c=(d=1,)), (c=(d=2,),))
(a = 1, b = 3, c = (d = 2,))
```
