```
@distributed
```

Dağıtık bellek, aşağıdaki biçimde paralel bir for döngüsü:

```
@distributed [reducer] for var = range
    body
end
```

Belirtilen aralık, tüm işçiler arasında bölünür ve yerel olarak yürütülür. Opsiyonel bir reducer fonksiyonu belirtilmişse, `@distributed` her işçi üzerinde yerel azaltmalar yapar ve çağıran süreçte son bir azaltma gerçekleştirir.

Bir azaltıcı fonksiyonu olmadan, `@distributed` asenkron olarak çalışır, yani tüm mevcut işçilerde bağımsız görevler başlatır ve tamamlanmayı beklemeden hemen döner. Tamamlanmayı beklemek için, çağrıyı [`@sync`](@ref) ile ön ekleyin, şöyle:

```
@sync @distributed for var = range
    body
end
```
