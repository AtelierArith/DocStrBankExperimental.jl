```
StackFrame
```

Yürütme bağlamını temsil eden yığın bilgisi, aşağıdaki alanlarla birlikte:

  * `func::Symbol`

    Yürütme bağlamını içeren fonksiyonun adı.
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    Yürütme bağlamını içeren MethodInstance veya CodeInfo (bulunabilirse) veya Modül (makro genişletmeleri için).
  * `file::Symbol`

    Yürütme bağlamını içeren dosyanın yolu.
  * `line::Int`

    Yürütme bağlamını içeren dosyadaki satır numarası.
  * `from_c::Bool`

    Kodun C'den gelmesi durumunda doğru.
  * `inlined::Bool`

    Kodun iç içe geçmiş bir çerçeveden gelmesi durumunda doğru.
  * `pointer::UInt64`

    `backtrace` tarafından döndürülen yürütme bağlamına işaretçi temsilidir.
