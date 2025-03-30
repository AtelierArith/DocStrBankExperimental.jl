```
LinRange{T,L}
```

`start` ve `stop` arasında `len` lineer olarak dağıtılmış elemanlardan oluşan bir aralık. Aralıkların boyutunu kontrol eden `len`, bir `Integer` olmalıdır.

# Örnekler

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

[`range`](@ref) kullanmaya kıyasla, doğrudan bir `LinRange` oluşturmak daha az yük getirmelidir ancak kayan nokta hatalarını düzeltmeye çalışmayacaktır:

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

Logaritmik olarak dağıtılmış noktalar için [`Logrange`](@ref Base.LogRange) ile de bakabilirsiniz.
