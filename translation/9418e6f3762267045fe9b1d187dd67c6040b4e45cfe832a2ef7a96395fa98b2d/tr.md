```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Belirli bir alanı verilen bir değere almak ve koşullu olarak ayarlamak için atomik olarak işlemleri gerçekleştirin.

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

Donanım tarafından destekleniyorsa, bu uygun donanım talimatına optimize edilebilir, aksi takdirde bir döngü kullanacaktır.

!!! compat "Julia 1.7"
    Bu fonksiyon Julia 1.7 veya daha yenisini gerektirir.

