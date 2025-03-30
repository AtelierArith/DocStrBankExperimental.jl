```
join([io::IO,] iterator [, delim [, last]])
```

Herhangi bir `iterator`'ı tek bir dizeye birleştirir, komşu öğeler arasında verilen ayırıcıyı (varsa) ekler. Eğer `last` verilmişse, son iki öğe arasında `delim` yerine kullanılacaktır. `iterator`'ın her bir öğesi `print(io::IOBuffer, x)` aracılığıyla bir dizeye dönüştürülür. Eğer `io` verilmişse, sonuç bir `String` olarak döndürülmek yerine `io`'ya yazılır.

# Örnekler

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```
