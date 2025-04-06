```
iscntrl(c::AbstractChar) -> Bool
```

Bir karakterin kontrol karakteri olup olmadığını test eder. Kontrol karakterleri, Unicode'un Latin-1 alt kümesinin yazdırılamayan karakterleridir.

# Örnekler

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
