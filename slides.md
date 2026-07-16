---
theme: seriph
background: /bg.jpg
title: JsShaker 项目进展报告
info: ""
mdc: true
colorSchema: light
# canvasWidth: 970
lineNumbers: true
fonts:
  # mono: 'DM Mono'
  sans: 'Noto Sans SC'
  strong: 'Rubik Iso'
  fast: 'Ubuntu'
  hand: 'Caveat'
---

# JsShaker {.font-serif}

<div op-80 class="text-2xl font-serif" pb-10>
项目进展报告
</div>

<div pt-4 pb-6>
熊桐睿 许逸凡 徐铭凯<br>
指导老师：张昱 丁伯尧
</div>

---

# 汇报内容

<div text-2xl leading-14 mt-6>

1. 开题时的目标
2. 各目标的进展情况和差距
3. 未来 3 个月工作计划、拟实现目标和难点
4. 预计经费支出（除人员费以外）
5. 人员变化情况

</div>

---

# 开题时的目标

<div mt-4 text-xl leading-10>

1. **实现 JavaScript 代码体积优化工具 JsShaker**
   - 基于“带有依赖追踪的抽象解释”，单轮分析完成优化
   - 兼顾语言动态性、编译速度与优化效果

2. **构建真实项目测试集，验证优化效果与性能开销**

3. **将 JsShaker 部署到华为鲲鹏算力平台，并做针对性调优**

4. **探索昇腾 AI 辅助的代码优化增强**

</div>

---

# 项目背景与技术路线（简述）

<div grid grid-cols-2 gap-8 mt-2>
<div>

- JavaScript/TypeScript 是使用最广的语言之一，应用平均依赖 **350** 个 npm 包，带来大量未使用代码

- 现有工具（Rollup、Terser 等）受限于可达性分析与模式化重写，优化空间有限

- 本项目通过**带有依赖追踪的抽象解释**，在**单次分析**中精确识别不可或缺与可安全删除的代码

</div>
<div>

<img src="./figures/workflow.png" mt-4 />

</div>
</div>

---

# 技术路线：核心机制

<div grid grid-cols-2 gap-8 mt-2>
<div>

**抽象值与抽象域**

- 用“抽象值”概括程序运行时一类可能的具体值，对真实数据做近似表示

<img w-0 min-w-full src="./figures/lattice.png" mt-2 />

</div>
<div>

**依赖追踪**

- 记录哪些代码节点参与生成了每个值
- 值产生副作用或逃逸时，将对应代码标记为不可删除
- 单次分析即可完成优化，避免多轮“分析—转换”的开销

</div>
</div>

---

# 技术路线：分析设计

<div mt--2 />

[控制流分析]{.text-2xl.text-primary} —— 处理确定性与非顺序控制流中的依赖传播

![1777953562326](./assets/1777953562326.png){.w-full.mt-1}

[数据流分析]{.text-2xl.text-primary} —— 面向对象语义与逃逸值的求值规则，单轮完成分析与优化

![](./figures/deps.png){.h-52.mt-1}

---

# 进展概览

<div mt-6 text-xl>

| 开题目标 | 进展情况 | 状态 |
| -- | -- | -- |
| 1. JsShaker 核心实现 | 核心分析、代码转换与高级优化均已完成 | <span text-green-700 font-bold>基本完成</span> |
| 2. 测试集构建与验证 | 已在 13 个真实项目用例上完成验证，效果达到预期 | <span text-green-700 font-bold>基本完成</span> |
| 3. 华为鲲鹏平台部署与调优 | 已完成部署与初步运行，调优工作进行中 | <span text-orange-600 font-bold>进行中</span> |
| 4. 昇腾 AI 辅助优化探索 | 已开展初步调研与尝试 | <span text-orange-600 font-bold>进行中</span> |

</div>

---

# 进展：优化效果

在所有测试用例上取得最优，*额外*删除 <strong>平均 27.6%，最高 66.7%</strong> 的代码体积：

![1777908797419](./assets/1777908797419.png){.w-208.ml--2}

---

# 进展：分析性能

函数摘要技术的引入，将优化速度提升了<strong>平均 1.58，最高 23.28 倍</strong>：

![1777973020931](./assets/1777973020931.png)

---

# 进展：华为平台部署与调优

<div mt-2 text-xl leading-10>

**鲲鹏算力底座**

- 已将 JsShaker 部署至华为鲲鹏服务器，完成初步运行与验证
- 正在针对鲲鹏平台特性开展调优，优化构建流程的整体效率

**昇腾智能增强**

- 围绕 AI 辅助代码优化开展了初步调研与尝试

</div>

---

# 目前存在的差距

<div mt-6 text-xl leading-12>

- 鲲鹏平台上的调优工作尚不充分，性能数据有待系统化收集与分析

- 大规模真实工程上的验证还不够充分，覆盖度有待进一步提升

- AI 辅助优化仍处于探索阶段，实际效果有待验证

</div>

---

# 未来 3 个月工作计划

<div mt-4 text-xl leading-10>

**工作计划**

1. 继续推进 JsShaker 在华为鲲鹏平台上的调优与大规模工程验证
2. 探索 AI 辅助的代码优化方向，形成初步原型
3. 完善工具的工程化程度与易用性

**拟实现目标**

- 在鲲鹏平台上形成稳定、可复现的优化与评测流程
- 完成 AI 辅助优化的原型验证

</div>

---

# 难点

<div mt-6 text-xl leading-12>

- JavaScript 语言动态性强，平台化落地过程中需要兼顾分析精度与运行效率

- 大规模真实工程情况复杂，验证与调优工作量大

- AI 辅助优化的效果存在不确定性，需要反复试验与调整

</div>

---

# 预计经费支出（除人员费以外）

<div mt-6 text-xl leading-12>

- **大模型 API token 费用**：用于 AI 辅助优化方向的探索、实验与评测，是下一阶段的主要支出

- **设备费用**：暂无大额设备采购计划，主要依托现有算力资源开展工作

</div>

---

# 人员变化情况

<div mt-8 text-2xl leading-14>

无人员变化。

项目组成员：**熊桐睿、许逸凡、徐铭凯**

</div>

---
layout: end
---

END

---

# 附录：核心设计

<div grid grid-cols-2 gap-12 mt-6>
<div px-2 py-0 flex-grow relative>

[抽象值]{.text-red-600.font-bold}：对程序运行时真实数据的一种近似表示

程序运行时的具体值有无穷种可能，不可能枚举。

于是用“抽象值”来概括一类可能的具体值——它可以是“某个数字”“某个字符串”，甚至精确到“数字 42”。整个取值集合叫做“[抽象域]{.text-red-600.font-bold}”：

<img w-0 min-w-full src="./figures/lattice.png" mb-4 />

</div><div px-2 py-0 flex-grow>

[依赖追踪]{.text-blue-600.font-bold}：本工作的核心机制

不仅计算一个变量“是什么”（抽象值），还维护一个集合，记录哪些代码节点（比如某行赋值、某个函数调用）参与生成了这个值。

当这个值最终产生副作用（比如打印输出）或从可分析代码逃逸时，系统就把集合里的代码节点标记为 [Live（不可删除）]{.text-red-600.font-bold}。

基于此，优化器能在**单次分析**中精确判断哪些代码不可或缺、哪些可以安全删除，避免了传统方法需要多轮“分析—转换”的高昂开销。

</div>
</div>

---

# 附录：测试集

13 个由真实 JavaScript 项目构建的测试用例：

![1777908747419](./assets/1777908747419.png)

---

# 附录：消融实验

左：分支折叠、常量折叠和属性名简化这三个高级优化分别贡献了平均 **12.0%**, **12.7%** 和 **3%** 的体积缩减。<br>
右：JsShaker 安全的属性名简化可以识别并优化平均约 **13.95%** 的可优化属性名。

![1777908828139](./assets/1777908828139.png){.mt--2}

---

# 附录：构建时间开销

左：JsShaker 平均引入了 **14%** 的额外构建时间；右：MaxRecDepth=2 时较好地平衡了分析速度和优化效果。

![1777908843177](./assets/1777908843177.png){.w-180.mt--2}
