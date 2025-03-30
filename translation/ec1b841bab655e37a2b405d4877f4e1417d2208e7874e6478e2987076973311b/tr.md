```
UndefKeywordError(var::Symbol)
```

Gerekli anahtar argüman `var`, bir fonksiyon çağrısında atanmadı.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function my_func(;my_arg)
           return my_arg + 1
       end
my_func (generic function with 1 method)

julia> my_func()
HATA: UndefKeywordError: anahtar argüman `my_arg` atanmadı
Stacktrace:
 [1] my_func() at ./REPL[1]:2
 [2] üst düzey kapsam at REPL[2]:1
```
