```
merge_analysis(repo::GitRepo, anns::Vector{GitAnnotated}) -> analysis, preference
```

对由注释分支提示 `anns` 指向的分支运行分析，并确定在什么情况下可以合并。例如，如果 `anns[1]` 只是 `ann[2]` 的一个祖先，那么 `merge_analysis` 将报告可以进行快速前进合并。

返回两个输出，`analysis` 和 `preference`。`analysis` 有几个可能的值：

  * `MERGE_ANALYSIS_NONE`：无法合并 `anns` 的元素。
  * `MERGE_ANALYSIS_NORMAL`：常规合并，当 HEAD 和用户希望合并的提交都从一个共同的祖先分歧。在这种情况下，必须解决更改，并可能会发生冲突。
  * `MERGE_ANALYSIS_UP_TO_DATE`：用户希望合并的所有输入提交都可以从 HEAD 到达，因此不需要进行合并。
  * `MERGE_ANALYSIS_FASTFORWARD`：输入提交是 HEAD 的后代，因此不需要进行合并 - 用户可以简单地检出输入提交。
  * `MERGE_ANALYSIS_UNBORN`：存储库的 HEAD 指向一个不存在的提交。无法合并，但可能可以检出输入提交。

`preference` 也有几个可能的值：

  * `MERGE_PREFERENCE_NONE`：用户没有偏好。
  * `MERGE_PREFERENCE_NO_FASTFORWARD`：不允许任何快速前进合并。
  * `MERGE_PREFERENCE_FASTFORWARD_ONLY`：仅允许快速前进合并，不允许其他类型（可能会引入冲突）。

`preference` 可以通过存储库或全局 git 配置进行控制。
