```
public
```

`public`, modüller içinde, Julia'ya modülün hangi isimlerinin kamu API'sinin bir parçası olduğunu belirtmek için kullanılır. Örneğin: `public foo`, `foo` isminin kamuya açık olduğunu belirtir, ancak modülü [`using`](@ref) kullanırken erişilebilir hale getirmez. Ayrıntılar için [modüller hakkındaki kılavuz bölümüne](@ref modules) bakın.

!!! compat "Julia 1.11"
    public anahtar kelimesi Julia 1.11'de eklendi. Öncesinde kamuya açıklık kavramı daha az belirgindi.

