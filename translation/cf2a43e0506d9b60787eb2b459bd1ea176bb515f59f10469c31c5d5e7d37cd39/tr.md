```
DateTime
```

`DateTime`, proleptik Gregory takvimine göre bir zaman noktasını temsil eder. Zamanın en ince çözünürlüğü milisaniyedir (yani, mikro saniyeler veya nano saniyeler bu türle temsil edilemez). Bu tür, sabit nokta aritmetiğini destekler ve bu nedenle alt akma (veya üst akma) eğilimindedir. Önemli bir sonuç, bir `Mikrosaniye` veya `Nanosaniye` eklerken yuvarlamadır:

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us 1000us'a yuvarlandı
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499 1000us'a yuvarlandı
2023-08-19T17:45:32.901
```
