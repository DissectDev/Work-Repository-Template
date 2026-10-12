# 工作仓库模板

以 Git 保存工作记录，从 MADR 决策文档开始。后续的调查、测试、复盘等模板可以加入同一个目录。

## 从哪里开始

| 我现在要做什么 | 入口 |
| --- | --- |
| 新写一份决策 | [简版 MADR](templates/madr.md) |
| 比较复杂方案、记录证据和验证方式 | [完整版 MADR](templates/madr-full.md) |
| 检查一份决策是否说清楚 | [七问评审](docs/guides/adr-review.md) |
| 查找已经作出的决策 | [决策目录](docs/decisions/README.md) |
| 查看调研与对比材料 | [调研目录](docs/research/README.md) |
| 查找或新增模板类型 | [模板目录](templates/README.md) |

## 一次性设置为 GitHub 模板仓库

1. 解压仓库包，在 GitHub 新建一个空仓库，例如 `work-repository-template`；建议先选择 Private。
2. 将本目录内部的文件和目录上传到该仓库根目录。让本 README 直接位于根目录，不要额外套一层 `work-repository-template/`。
3. 打开仓库 **Settings → General**，勾选 **Template repository**。此操作需要仓库管理员权限。
4. 以后创建工作仓库时，选择 **Use this template → Create a new repository**。

也可以在已安装并登录 GitHub CLI 的电脑上执行以下命令。在解压后的本目录中运行；先确认同名仓库尚不存在。第一条 `git commit` 使用你自己的 Git 身份配置。

```bash
git init -b main
git add .
git commit -m "Initialize work repository template"
gh repo create work-repository-template --private --source=. --remote=origin --push
gh repo edit --template
```

模板属性保存在 GitHub 的仓库设置中，不能只靠压缩包中的文件启用。

## 新建一份决策

在生成的工作仓库根目录执行（编号和名称按实际修改；`-n` 避免覆盖同名文件）：

```bash
cp -n templates/madr.md docs/decisions/0001-image-build-strategy.md
```

填写文档，然后按通常的 Git 工作流提交。需要更多细节时，复制 `templates/madr-full.md`。也可以让 Agent 完成复制、命名和起草。

一份记录对应一个重要选择。普通执行任务可以直接使用任务清单；尚未澄清的问题可以先在讨论中展开，再形成决策记录。

## 状态与更新

* `proposed`：仍在讨论，允许修改。
* `accepted`：选择已被接受，实施进度由关联任务记录。
* `rejected`：方案被否决，保留原因。
* `superseded`：后续决策已经取代它，链接替代记录。

已接受决策的重大取舍改变时，新增记录并相互链接。模板库的更新用于改善未来文档；历史记录保留当时的理由。

GitHub 的模板功能复制整个仓库，生成新仓库的独立历史。后续模板变更不会自动同步到已生成仓库，可按需人工挑选变更。

## 扩展其他类型

将新模板加入 `templates/`，并在 [模板目录](templates/README.md) 登记用途和实例保存位置。实例保存到相应的工作目录，避免把真实项目内容混入模板。

当前只提供 MADR，两种版本共享同一语义。七问评审独立保存，可按决策的重要性使用。

## 参考

* [MADR 4.0.0 官方模板](https://github.com/adr/madr/tree/4.0.0/template)
* [创建 GitHub 模板仓库](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository)
* [从模板创建仓库](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)

MADR 中文版为改编模板；来源和使用许可见 [模板目录](templates/README.md)。这不是 MADR 官方中文发布。
