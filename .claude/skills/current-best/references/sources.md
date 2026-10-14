# 数据源清单

地址和接口会变。打不开时先搜索榜单名称确认新地址；确认地址已变，就更新本文件。最后整理：2026-10-14。

* [综合聚合](#综合聚合)
* [编码与智能体](#编码与智能体)
* [其他模型类别](#其他模型类别)
* [非模型实体](#非模型实体)
* [发现新实体的检索方法](#发现新实体的检索方法)

## 综合聚合

### BenchLM

* 首页：<https://benchlm.ai/>。分类页如 <https://benchlm.ai/coding>、<https://benchlm.ai/agentic>；单项基准页形如 `https://benchlm.ai/benchmarks/<slug>`（如 `swe-bench-verified`、`terminal-bench-2`、`livecodebench-v6`）；性价比榜如 <https://benchlm.ai/best/best-value-coding>。
* 单项基准页的数据部分汇编自厂商自报和二手报道。逐行看来源标注，自报数字要用独立运行的结果核对。
* 数据接口（据 <https://benchlm.ai/data> 页面说明，调用前先看该页确认参数）：
  * `GET https://benchlm.ai/api/data/leaderboard?category=coding&limit=10`：按分类取排名；`format` 默认 JSON，也可取 CSV。
  * `GET https://benchlm.ai/api/data/benchmarks`：按模型 slug 取该模型的各项基准分数。
  * `https://benchlm.ai/llms.txt` 与 `llms-full.txt`：供模型读取的站点说明。页面另有 Markdown 版，如 <https://benchlm.ai/md/about.md>。
* 方法：<https://benchlm.ai/methodology>。分类分数由多个基准加权、归一化后合成；据此下结论前，先确认参与计算的是哪些基准。
* 两条榜：provisional 收录来源可靠的公开数据，verified 只收精确来源。结论优先引用 verified；只出现在 provisional 里的新模型要注明。
* 速度数据来自 Artificial Analysis。不同页面写的模型和基准总数不一致，引用数量时以接口返回为准。

### Artificial Analysis

* <https://artificialanalysis.ai/leaderboards/models>：独立运行的综合智能指数，以及价格、输出速度和延迟。适合“性价比”“速度”类问题。
* 同站还有语音合成、图像编辑、文生视频、音乐等竞技场式榜单，路径如 `/text-to-speech/leaderboard`、`/video/leaderboard/text-to-video`。

### Epoch AI Benchmarking Hub

* <https://epoch.ai/benchmarks>：第三方独立运行的基准结果，用来核对厂商自报分数。

### Vals AI

* 独立运行若干基准，页面写明评测框架和更新日期，如 <https://www.vals.ai/benchmarks/swebench>、<https://www.vals.ai/benchmarks/terminal-bench-2-1>。适合核对 BenchLM 中的自报数字。

### LMArena

* <https://lmarena.ai/leaderboard>：人类两两投票得到的偏好排名（Bradley-Terry 分），分 Text、Code/WebDev、Vision 等榜。
* <https://news.lmarena.ai/leaderboard-changelog/>：榜单变更日志，是发现新上榜模型的好入口。
* 偏好分受回答风格和长度影响，与能力类基准分开表述。

### OpenRouter Rankings

* <https://openrouter.ai/rankings>：按 OpenRouter 上的 token 用量排序，反映采用度，不代表质量。适合发现新模型、了解实际使用情况。

## 编码与智能体

* SWE-bench：<https://www.swebench.com/>，Verified 榜见 <https://www.swebench.com/verified.html>，另有 Multilingual 等子榜。分数强烈依赖 agent 框架；比较模型时看同一框架（如 bash-only 的 mini-SWE-agent）的同一大版本。头部已接近饱和，小分差不足以排序。
* Terminal-Bench：<https://www.tbench.ai/leaderboard>。按“agent + 模型”组合排名；留意基准版本（2.0、2.1 等）和 verified 筛选。2.1 的结果还分别发布在 Artificial Analysis（<https://artificialanalysis.ai/evaluations/terminalbench-2-1>）、Vals AI 和 Snorkel（<https://snorkel.ai/leaderboard/terminal-bench-2-1/>）等处，各用不同的 agent 框架，不能混排。
* LMArena Code/WebDev：<https://lmarena.ai/leaderboard/code>。人类偏好，侧重网页与前端生成。
* Aider leaderboards：<https://aider.chat/docs/leaderboards/>。多语言代码编辑。更新频率不稳定，先看页面日期。
* Berkeley Function Calling Leaderboard（BFCL）：<https://gorilla.cs.berkeley.edu/leaderboard.html>。工具与函数调用。

## 其他模型类别

* 文本向量（embedding）：MTEB，<https://huggingface.co/spaces/mteb/leaderboard>。先选对子榜（多语言、中文、代码检索等）；结果多为自报，排名方法也调整过。
* 语音识别：Open ASR Leaderboard，<https://huggingface.co/spaces/hf-audio/open_asr_leaderboard>。比较 WER 和速度（RTFx），分英语、多语言、长音频等赛道。
* 语音合成、图像、视频、音乐生成：Artificial Analysis 与 LMArena 的对应竞技场榜。
* 其他专项（OCR、文档解析、翻译、多模态理解等）：搜 `<任务> benchmark leaderboard <年份>`，优先由基准作者维护、写有更新日期的页面。Papers with Code 已于 2025 年停止服务，旧链接里的 SOTA 表不再更新，不要当作当前结果引用。

## 非模型实体

库、工具、数据库和服务通常没有统一榜单，改用活跃度与生命周期证据：

* 项目活跃度：GitHub 的 Releases、最近提交、issue 响应。看最新 release 日期，不要只看 star 总数。
* 版本与支持状态：<https://endoflife.date/>。
* 下载趋势：npm 用 <https://npmtrends.com/>，PyPI 用 <https://pypistats.org/>，crates.io 看包页面的下载数。
* 数据库流行度：DB-Engines Ranking，<https://db-engines.com/en/ranking>，每月更新，按类别有子榜。它统计搜索与社交提及，衡量的是热度，不是性能或装机量。
* 性能基准：向量检索看 <https://ann-benchmarks.com/>；Web 框架看 TechEmpower Framework Benchmarks（按轮次发布，先看轮次日期）。
* 年度调查（Stack Overflow Developer Survey、State of JS 等）：一年一次，适合看趋势，不适合判断“本月最好”。

## 发现新实体的检索方法

* 检索词里写当前月份和年份；中文、英文各搜一次。
* 按月的发布追踪页：搜 `AI models released <月份 年份>`。这类页面多为二手汇总，只用来发现候选。
* 二手汇总站更新节奏不一。2026-10 试用时，llm-stats.com 的 SWE-bench Verified 榜首仍停在上一代模型，而 BenchLM 与 Vals AI 已更新。
* `<功能> new OR launch OR release <月份 年份>`、`<榜首候选> vs`、`<榜首候选> alternative`。
* 榜单 changelog、厂商博客与发布说明、arXiv 近期论文中关于 `state of the art on <基准>` 的表述。
* Hacker News、Reddit 等社区只用来发现候选，不用来确定分数。
