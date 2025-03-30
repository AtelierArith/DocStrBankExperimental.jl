```
@s_str -> DeğiştirmeDizesi
```

Düzenli ifade değiştirmeleri için kullanılan bir değiştirme dizesi oluşturur. Dizedeki `\N` biçimindeki diziler, düzenli ifadede N'inci yakalama grubuna atıfta bulunur ve `\g<groupname>` biçimi, `groupname` adıyla adlandırılmış bir yakalama grubuna atıfta bulunur.

# Örnekler

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```
