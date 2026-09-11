---
status: proposed
# 以下元数据可选；日期、人员等按实际情况填写。
# date: YYYY-MM-DD
# decision-makers: []
# consulted: []
# informed: []
---

# {决策的简短标题}

<!--
中文填写版：以 MADR 4.0.0 为基础，保留英文标题，填写说明为中文。
建议复制为 docs/decisions/NNNN-short-title.md，再填写大括号中的占位内容。
最小使用：保留 Context and Problem Statement、Considered Options、Decision Outcome
及其下的 Consequences；其余部分可按需要删除。元数据也可选。
评审七问独立保存在 docs/guides/adr-review.md，并非 MADR 模板强制要求。
本文件是一份待填写的模板，不表示任何方案已经获准或实施。
-->

## Context and Problem Statement

{用两三句话说明当前处境、要解决的问题，以及为什么此时需要作出选择。}

{明确本次决策的范围；将观测事实与尚待核实的假设分开。可链接需求、讨论或调查记录。}

## Decision Drivers

<!-- 可选。填写提示：区分必须满足的条件与偏好；冲突时注明优先级。 -->

* {必须满足的条件及其依据}
* {最重要的评价标准}
* {时间、成本、维护负担等其他相关标准}

## Considered Options

* {方案 A}
* {方案 B}
* {其他实际可行的方案；适用时包含维持现状、复用或暂缓}

## Decision Outcome

选择：{方案名称}。

理由：{将选定方案与本次需求、约束和优先级对应起来，解释为何接受它的取舍。}

<!-- 尚未决定时保留 proposed，并写明当前倾向与未解决的问题。 -->

### Consequences

* 正面：{预期获得什么，以及成立条件}
* 负面：{接受了哪些成本、限制或后续工作}
* 中性：{其他变化；无则删除}

### Confirmation

<!-- 可选：确认实现是否符合决策。不要把计划中的验证写成已完成的事实。 -->

* 确认方式：{检查、测试或评审方法；可链接具体流程}
* 通过条件：{可观察的要求}
* 证据位置：{执行后填写结果链接和对应版本；未执行则注明待验证}

## Pros and Cons of the Options

<!-- 可选。使用一致的评价标准比较；长篇研究另存并在此引用。 -->

### {方案 A}

* 支持：{理由及证据}
* 反对：{理由及证据}
* 中性：{相关但不改变倾向的事实；无则删除}

### {方案 B}

* 支持：{理由及证据}
* 反对：{理由及证据}
* 中性：{相关但不改变倾向的事实；无则删除}

## More Information

<!-- 可选。以下细分提示为本中文版本的整理，不是新增的 MADR 必填字段。 -->

* 证据与置信度：{哪些已经核实，哪些仍不确定；避免无依据的精确概率}
* 实施安排：{关联任务、执行入口或计划；这里只放必要引用}
* 效果复查：{何时检查是否改善了最初处境；采用什么观察指标}
* 重审条件：{哪些新事实、约束变化或失败结果会触发重新决策}
* 相关记录：{依赖、取代或受本决策影响的 ADR 链接}

## Template References

本文件是中文改编版，不是 MADR 官方中文发布。MADR 上游模板以 MIT OR CC0-1.0 双许可发布；本文件对模板部分选择 CC0-1.0。七问评审的摘要独立保存在配套指南中，原文权利归其作者所有。

* [MADR 4.0.0 完整模板](https://github.com/adr/madr/blob/4.0.0/template/adr-template.md)
* [MADR 4.0.0 最小模板](https://github.com/adr/madr/blob/4.0.0/template/adr-template-minimal.md)
* [MADR 项目与许可说明](https://adr.github.io/madr/)
* [七问评审清单原文](https://ozimmer.ch/practices/2023/04/05/ADRReview.html#adr-checklist)
* [START：决策准备条件](https://ozimmer.ch/practices/2023/12/01/ADDefinitionOfReady.html)
* [ecADR：决策完成条件](https://ozimmer.ch/practices/2020/05/22/ADDefinitionOfDone.html)

维护提示：proposed 表示仍在讨论。重大取舍改变时，可创建新 ADR 并将旧记录标记为 superseded，关联替代记录。accepted 表示决定已被接受，不等同于实施完成。
