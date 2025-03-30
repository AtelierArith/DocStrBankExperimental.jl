```
MultiSelectMenu
```

一个允许用户从列表中选择多个选项的菜单。

# 示例输出

```julia-repl
julia> request(MultiSelectMenu(options))
选择您喜欢的水果：
[按: Enter=切换, a=全选, n=全不选, d=完成, q=中止]
   [ ] 苹果
 > [X] 橙子
   [X] 葡萄
   [ ] 草莓
   [ ] 蓝莓
   [X] 桃子
   [ ] 柠檬
   [ ] 青柠
您喜欢以下水果：
  - 橙子
  - 葡萄
  - 桃子
```
