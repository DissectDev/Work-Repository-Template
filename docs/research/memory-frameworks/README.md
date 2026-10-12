# Agent 记忆框架对比（2026-10）

可排序的对比面板：[index.html](index.html)。在浏览器中直接打开即可，数据内嵌在页面里，无需构建。

## 范围

对比 Cognee、Hindsight、Mem0、Zep、GraphRAG 五个框架：

* DolphinBench 官方运行结果（通过率、总成本、延迟、各角色得分）
* 记忆抽取流水线（写入步骤、是否需要 LLM、事实变化时的处理、检索方式、记忆作用域）
* 向量数据库后端（可选存储、默认存储、图与元数据存放位置）
* API 设计：remember、recall、improve、forget 四个动作的对应调用
* 面向 Agent 应用的搭建复杂度（最快上手路径、本地依赖、生产自托管、托管服务、Agent 集成）

顶部控制栏可以切换 DolphinBench 运行配置，并按通过率、成本、API 契合度、搭建难度、后端数量、发布时间或名称重排所有区块；每张表也可以点击表头单独排序。

## 主要结论（数据截至 2026-10-12）

* DolphinBench 由 Mem0 发布（2026-09）。官方结果只覆盖五者中的 Mem0 和 Hindsight；Cognee、Zep、GraphRAG 没有官方运行。
* Hermes + GPT 5.6 Luna：Mem0 通过 424/600（70.67%，总成本 $96.21，中位延迟 37.7 s）；Hindsight 通过 417/600（69.50%，$84.65，55.3 s）。
* Hermes + MiniMax M3：Mem0 47.83%，Hindsight 41.00%。Claude Code + Sonnet 5 只测了 Mem0（32.33%），未纳入本对比的 Honcho 更高（35.83%）。
* Cognee 1.x 直接以 remember / recall / improve / forget 命名核心 API，且可在没有 LLM key 的情况下本地运行。
* Zep 只提供云服务（社区版已弃用），自托管需要改用 Graphiti 并自备图数据库。
* GraphRAG 处于维护模式，以批处理建索引，没有删除 API，也没有按用户划分的记忆，不适合逐条写入的 Agent 记忆场景。

## 评分口径

* API 契合度：每个动作 0–3 分（3 同名原生调用，2 一次调用直接完成，1 只能通过批处理、后台行为或手工修改间接完成，0 不支持），合计 0–12。
* 搭建复杂度：1（很容易）到 5（繁重），考虑需要运行的服务、是否必须有 LLM key、是否支持按用户划分记忆、是否支持增量写入。
* 两项都是依据 2026-10-12 的文档与安装路径作出的判断，不是测量值。

## 来源

* DolphinBench 官方运行记录：[mem0ai/dolphinbench](https://github.com/mem0ai/dolphinbench) 的 `results/` 与 `website/content/official-results.json`；论文 [arXiv 2609.24971](https://arxiv.org/abs/2609.24971)
* 各项目仓库 README、源码与文档：[Cognee](https://github.com/topoteretes/cognee)、[Hindsight](https://github.com/vectorize-io/hindsight)、[Mem0](https://github.com/mem0ai/mem0)、[Zep](https://github.com/getzep/zep) 与 [Graphiti](https://github.com/getzep/graphiti)、[GraphRAG](https://github.com/microsoft/graphrag)
* 版本与发布日期：PyPI（cognee 1.6.3、hindsight-api 0.10.3、mem0ai 2.2.1、zep-cloud 3.30.0、graphiti-core 0.30.2、graphrag 3.3.0）

页面中“其他已发布结果”一表引用各厂商自报的 LongMemEval、LoCoMo、BEAM 等成绩，条件各不相同，只作背景参考。

## 更新

数据集中在 `index.html` 末尾脚本的 `RUNS`（DolphinBench 运行）、`FW`（框架属性）和 `OTHER`（其他基准）三个常量中。更新数据后同步修改页面中的日期说明和本文件的结论。
