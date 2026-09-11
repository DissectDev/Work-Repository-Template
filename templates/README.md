# 模板目录

| 类型 | 模板 | 适用情况 | 实例保存位置 |
| --- | --- | --- | --- |
| MADR 简版 | [madr.md](madr.md) | 背景、选项、选择理由与后果已经足以说明决策 | `docs/decisions/NNNN-short-title.md` |
| MADR 完整版 | [madr-full.md](madr-full.md) | 需要展开约束、比较、证据、验证及重审条件 | `docs/decisions/NNNN-short-title.md` |

配套方法：[七问评审](../docs/guides/adr-review.md)。

## 新增类型

1. 将模板保存为一个 Markdown 文件，例如 `research.md`。
2. 在表格中登记用途与实例位置。
3. 写清需要填写的内容，并标记可选部分；引用外部模板时保留来源和许可说明。
4. 实际使用时复制模板，按项目填写实例。

无需为每种模板新建仓库。若以后确实需要参数问答或自动更新，可以再加入生成工具。

## 来源与许可

`madr.md` 与 `madr-full.md` 基于 [MADR 4.0.0](https://github.com/adr/madr/tree/4.0.0/template) 改编。上游以 MIT OR CC0-1.0 双许可发布；此处模板部分选择 CC0-1.0。参见 [MADR 许可说明](https://adr.github.io/madr/#license)。

中文版中的填写提示与目录组织是本仓库的补充。七问评审是对公开文章的简要概括，原文权利归作者所有。上述许可说明只描述模板来源，不为以后放入本仓库的项目代码、资料或记录指定许可。
