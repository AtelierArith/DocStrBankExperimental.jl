```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

Konstruiere ein [`Ordering`](@ref) Objekt aus denselben Argumenten, die von [`sort!`](@ref) verwendet werden. Elemente werden zuerst durch die Funktion `by` transformiert (die möglicherweise [`identity`](@ref) ist) und dann gemäß der Funktion `lt` oder einer bestehenden Ordnung `order` verglichen. `lt` sollte [`isless`](@ref) oder eine Funktion sein, die denselben Regeln wie der `lt` Parameter von [`sort!`](@ref) gehorcht. Schließlich wird die resultierende Ordnung umgekehrt, wenn `rev=true`.

Es ist nicht erlaubt, ein `lt` zu übergeben, das nicht `isless` ist, zusammen mit einer `order`, die nicht [`Base.Order.Forward`](@ref) oder [`Base.Order.Reverse`](@ref) ist; andernfalls sind alle Optionen unabhängig und können in allen möglichen Kombinationen zusammen verwendet werden.
