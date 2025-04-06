```
Dates.RFC1123Format
```

Tarih ve saat için RFC1123 formatlamasını açıklar.

# Örnekler

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), RFC1123Format)
"Çar, 08 Ağu 2018 12:00:43"
```
