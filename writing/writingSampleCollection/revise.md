# Introduction 衔接优化方案（针对 `finalDraft.md`）

## 目标
把 Introduction 从“信息点堆叠”改成“问题链条推进”：
1) 为什么 HI 重要 → 2) 为什么原始数据难以直接用 → 3) 为什么现有方法比较仍不充分 → 4) 本文如何回应。

---

## 一、目前不流畅的关键位置

### 1) P1（重要性）到 P2（数据问题）切换偏硬
- 当前状态：P1 结尾直接跳到“Because surveillance programs cannot assay...”。
- 问题：缺少“为什么现实实践会导致这个数据形态”的过渡桥。

### 2) P2（数据挑战）到 Move 2（文献缺口）缺“因此要比较方法”的显式句
- 当前状态：P2 最后一句已说“motivate computational models”，但下一段直接进入“Despite rapid progress...”。
- 问题：读者仍会觉得“为什么不是继续谈建模细节，而是转向文献比较”。

### 3) Move 2 到 Move 3 的任务界定可以更“接题”
- 当前状态：Move 2 说 trade-off，Move 3 说 review compares families。
- 问题：缺一条“因此本文的具体比较框架是什么”的承接句（可压缩到 Move 3 首句内）。

---

## 二、修改原则（只改衔接，不改核心论点）

- 不新增新文献争议，不扩大事实性主张。
- 每段结尾都回答下段开头的问题。
- 每个转折使用单一功能连接词，避免同一段内多次“However/Moreover”堆叠。
- 保持现在的谨慎语气（例如 limited / shaped by）。

---

## 三、段间“桥句”建议（可直接替换）

## A. P1 末尾新增承接句（连接到 P2）
在 P1 最后一句后增加一句：

> Yet this practical value depends on data coverage that surveillance systems cannot fully provide in routine operation.

作用：把“公共卫生价值”自然引到“数据不完备”的现实约束。

---

## B. P2 末尾改为“方法比较需求”导向（连接到 Move 2）
将 P2 最后一句替换为：

> These constraints make computational modeling necessary, but they also make model choice consequential: different methods respond to sparsity, heterogeneity, and forward prediction demands in different ways.

作用：从“需要模型”推进到“需要比较模型”，为 Move 2 铺路。

---

## C. Move 2 首句微调（减少突兀）
将 Move 2 第一二句压成“承接型开头”：

> In response to these data constraints, computational HI prediction has progressed rapidly. However, the literature still lacks a clear comparative account of how different modeling assumptions shape performance under realistic surveillance conditions.

作用：先承接上段“需要建模”，再提出“比较不足”的gap。

---

## D. Move 2 末句微调（避免悬空）
将 Move 2 最后一句改为：

> These trade-offs are therefore rarely compared in a structured way across method families, especially in terms of interpretability, calibration under sparse heterogeneous observations, and prospective utility.

作用：把下一段将采用的比较维度提前点名，减少逻辑跳跃。

---

## E. Move 3 首句增强“回应关系”
将 Move 3 首句改为：

> To address this comparison gap, this review examines three major families of computational HI prediction methods—geometry-based, matrix-based, and sequence-based approaches—through the assumptions they make about virus–serum interaction.

作用：明确“本文是对上一段 gap 的回应”，形成闭环。

---

## 四、建议的 Introduction 内部结构（最终顺序不变）

- P1：问题重要性（公共卫生）+ 一句现实约束桥。
- P2：数据挑战链（不完备→覆盖不均→censoring→heterogeneity）+ 一句“模型比较必要”。
- Move 2：现有研究进展 + 比较不足（gap）。
- Move 3：本文比较框架与贡献边界（不是“首创”，而是“结构化比较”）。

---

## 五、可选：一版“低改动”连贯性增强模板（仅替换衔接句）

你可以只做下面 4 处改动，不动段落主体内容：
1. 在 P1 末尾加桥句（A）。
2. 替换 P2 末句为比较导向句（B）。
3. 替换 Move 2 开头为承接型双句（C）。
4. 替换 Move 3 首句为回应型句子（E）。

这样可以在不重写段落的前提下，明显提升“段间因果推进感”。

---

## 六、自检清单（修改后快速检查）

- 读完 P1，是否自然产生“那数据够不够”的问题？
- 读完 P2，是否自然产生“那该选什么模型”的问题？
- 读完 Move 2，是否自然产生“本文怎么比较”的问题？
- Move 3 首句是否明确回答了上一个问题？

如果以上四项都为“是”，intro 的主线就会明显顺滑。
