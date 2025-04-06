```
struct SimpleColor
```

Bir rengin temel bir temsilidir, dize stilizasyonu amaçları için tasarlanmıştır. Ya bir adlandırılmış rengi (örneğin `:red`) ya da 8 bit derinliğinde `r`, `g`, `b` rengini belirten bir NamedTuple olan `RGBTuple` içerebilir.

# Yapıcılar

```julia
SimpleColor(name::Symbol)  # örn. :red
SimpleColor(rgb::RGBTuple) # örn. (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # örn. 0x123456
```

Ayrıca `tryparse(SimpleColor, rgb::String)`'e de bakın.
