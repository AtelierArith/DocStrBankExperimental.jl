```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

表示一个排序函数应该使用部分快速排序算法。`PartialQuickSort(k)` 类似于 `QuickSort`，但只需要找到并排序那些在 `v` 完全排序时会出现在 `v[k]` 中的元素。

特点：

  * *不稳定*：不保留比较相等的元素的顺序（例如，在忽略大小写的字母排序中，“a”和“A”）。
  * *原地* 在内存中。
  * *分治法*：排序策略类似于 [`MergeSort`](@ref)。

请注意，`PartialQuickSort(k)` 不一定会对整个数组进行排序。例如，

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```
