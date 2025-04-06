```
单选菜单
```

允许用户从列表中选择一个选项的菜单。

# 示例输出

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
选择你最喜欢的水果：
^  葡萄
   草莓
 > 蓝莓
v  桃子
你最喜欢的水果是蓝莓！
```
