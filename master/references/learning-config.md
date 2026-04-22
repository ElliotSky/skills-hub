# 学习配置系统

## 配置文件位置

`<topic-slug>/learning-config.yaml`

每个主题独立配置，首次启动时由导师根据学生意图初始化，学生可随时调整。

---

## 配置项说明

```yaml
# ============================================================
# 学习节奏配置
# ============================================================

learning_pace:
  # 知识传递速度
  # - sprint: 快速浏览模式，优先覆盖广度，每轮 5-8 个新概念
  # - standard: 平衡模式，每轮 2-4 个新概念
  # - deep: 深度模式，每轮 1-2 个新概念，充分展开
  speed: standard
  
  # 验证频率
  # - low: 每 8-10 个概念验证一次
  # - medium: 每 4-6 个概念验证一次
  # - high: 每 2-3 个概念验证一次
  verification_frequency: medium

# ============================================================
# 教学风格配置
# ============================================================

teaching_style:
  # 知识给出方式（核心配置）
  # - direct: 直接讲授为主（70% 直接给出，20% 引导推导，10% 苏格拉底式）
  # - guided: 引导推导为主（30% 直接给出，50% 引导推导，20% 苏格拉底式）
  # - socratic: 苏格拉底式为主（10% 直接给出，30% 引导推导，60% 苏格拉底式）
  delivery_mode: guided
  
  # 基础概念处理策略
  # - give_directly: 术语、定义、公理直接给出
  # - minimal_derivation: 给出定义后，引导推导"为什么需要它"
  # - full_derivation: 尝试让学生从已知概念推导新概念
  foundational_concepts: give_directly
  
  # 提问密度
  # - low: 主要陈述，偶尔提问
  # - medium: 陈述与提问交替
  # - high: 以提问为主，少量陈述
  question_density: medium
  
  # 反例使用频率
  # - rare: 仅在关键概念使用
  # - moderate: 每 2-3 个概念给一个反例
  # - frequent: 几乎每个概念都给反例
  counterexample_frequency: moderate

# ============================================================
# 记忆策略配置
# ============================================================

memory_strategy:
  # 记忆方式偏好
  # - understanding_first: 优先深度理解，记忆是副产品（默认苏格拉底式）
  # - balanced: 理解与记忆并重
  # - memorization_aided: 允许先快速记忆框架，再回溯理解
  approach: balanced
  
  # 是否使用记忆辅助工具
  # - true: 主动提供记忆口诀、助记符、对比表格
  # - false: 不主动提供，除非学生要求
  use_mnemonics: true
  
  # 重复策略
  # - minimal: 不主动重复，依赖学生自主复习
  # - spaced: 在后续阶段自然穿插前置概念
  # - explicit: 每个阶段结束时显式复习前置概念
  repetition: spaced

# ============================================================
# 深度控制配置
# ============================================================

depth_control:
  # 第一性原理使用频率
  # - rare: 仅在跨阶段串联时使用
  # - key_concepts: 对核心概念使用
  # - pervasive: 几乎每个概念都追溯到第一性原理
  first_principles_frequency: key_concepts
  
  # 哲学追问深度
  # - surface: 不追问本体论/认识论问题
  # - moderate: 对关键概念追问"为什么是这样"
  # - deep: 对大部分概念追问三层（本体/认识论/价值）
  philosophical_depth: moderate
  
  # 边界探索
  # - skip: 不主动探索概念适用边界
  # - on_demand: 学生问到时才探索
  # - proactive: 主动给出边界情形和反例
  boundary_exploration: on_demand

# ============================================================
# 输出风格配置
# ============================================================

output_style:
  # 单次输出长度
  # - concise: 1-2 段，快速迭代
  # - moderate: 3-5 段
  # - detailed: 6+ 段，一次性展开较多内容
  response_length: moderate
  
  # 是否使用可视化
  # - true: 主动使用 Mermaid 图、表格、公式
  # - false: 纯文字为主
  use_visualization: true
  
  # 语言风格
  # - formal: 学术化表达
  # - conversational: 对话式表达
  # - mixed: 根据内容类型自适应
  tone: conversational

# ============================================================
# 特殊模式
# ============================================================

special_modes:
  # 考试冲刺模式（临时覆盖其他配置）
  # - false: 正常学习
  # - true: 优先覆盖考点，提供记忆框架，减少深度追问
  exam_prep_mode: false
  
  # 快速预览模式（临时覆盖其他配置）
  # - false: 正常学习
  # - true: 30-60 分钟快速建立全景图，标记"深挖点"供后续回溯
  quick_preview_mode: false
```

---

## 预设配置模板

### 模板 1: 快速构建知识体系（解决当前痛点）

```yaml
learning_pace:
  speed: sprint
  verification_frequency: low

teaching_style:
  delivery_mode: direct
  foundational_concepts: give_directly
  question_density: low
  counterexample_frequency: rare

memory_strategy:
  approach: memorization_aided
  use_mnemonics: true
  repetition: explicit

depth_control:
  first_principles_frequency: rare
  philosophical_depth: surface
  boundary_exploration: skip

output_style:
  response_length: detailed
  use_visualization: true
  tone: conversational

special_modes:
  exam_prep_mode: false
  quick_preview_mode: true
```

**适用场景**：
- 完全陌生的领域，需要先建立全景图
- 时间紧迫，需要快速掌握框架
- 准备后续深入学习的"侦察阶段"

---

### 模板 2: 平衡模式（当前默认）

```yaml
learning_pace:
  speed: standard
  verification_frequency: medium

teaching_style:
  delivery_mode: guided
  foundational_concepts: minimal_derivation
  question_density: medium
  counterexample_frequency: moderate

memory_strategy:
  approach: balanced
  use_mnemonics: true
  repetition: spaced

depth_control:
  first_principles_frequency: key_concepts
  philosophical_depth: moderate
  boundary_exploration: on_demand

output_style:
  response_length: moderate
  use_visualization: true
  tone: conversational

special_modes:
  exam_prep_mode: false
  quick_preview_mode: false
```

**适用场景**：
- 有一定基础，希望系统学习
- 理解与记忆并重
- 不确定自己的学习风格时的默认选择

---

### 模板 3: 深度理解模式（原苏格拉底式）

```yaml
learning_pace:
  speed: deep
  verification_frequency: high

teaching_style:
  delivery_mode: socratic
  foundational_concepts: full_derivation
  question_density: high
  counterexample_frequency: frequent

memory_strategy:
  approach: understanding_first
  use_mnemonics: false
  repetition: minimal

depth_control:
  first_principles_frequency: pervasive
  philosophical_depth: deep
  boundary_exploration: proactive

output_style:
  response_length: concise
  use_visualization: true
  tone: conversational

special_modes:
  exam_prep_mode: false
  quick_preview_mode: false
```

**适用场景**：
- 已有框架，想深度理解核心概念
- 复盘阶段，重构知识体系
- 追求"知其所以然"的学习者

---

### 模板 4: 考试冲刺模式

```yaml
learning_pace:
  speed: sprint
  verification_frequency: medium

teaching_style:
  delivery_mode: direct
  foundational_concepts: give_directly
  question_density: low
  counterexample_frequency: moderate

memory_strategy:
  approach: memorization_aided
  use_mnemonics: true
  repetition: explicit

depth_control:
  first_principles_frequency: rare
  philosophical_depth: surface
  boundary_exploration: skip

output_style:
  response_length: detailed
  use_visualization: true
  tone: formal

special_modes:
  exam_prep_mode: true
  quick_preview_mode: false
```

**适用场景**：
- 考试前 1-2 周
- 需要快速记忆大量知识点
- 优先覆盖考纲，暂时放弃深度理解

---

## 配置调整流程

### 首次启动时

导师询问：
```
在开始之前，我想了解你的学习偏好：

1. 你希望的学习节奏是？
   A. 快速浏览，先建立全景图（sprint）
   B. 平衡推进，理解与记忆并重（standard）
   C. 深度探究，充分理解每个概念（deep）

2. 对于新概念，你更倾向于？
   A. 直接告诉我是什么，我先记住（direct）
   B. 给我一些提示，让我尝试推导（guided）
   C. 通过提问引导我自己得出结论（socratic）

3. 你的学习目标是？
   A. 快速掌握框架，后续再深入
   B. 系统学习，建立完整知识体系
   C. 深度理解核心原理
   D. 应对考试/面试

我会根据你的选择生成配置文件，你随时可以调整。
```

根据回答自动选择模板并生成 `<topic-slug>/learning-config.yaml`。

### 学习过程中调整

学生可以随时说：
- "节奏太慢了，加快一点" → 调整 `speed` 和 `delivery_mode`
- "我想深入理解这个概念" → 临时切换到 `socratic` 模式
- "先别问了，直接告诉我" → 临时切换到 `direct` 模式
- "用考试冲刺模式" → 加载模板 4
- "重置为默认配置" → 加载模板 2

导师执行：
1. 更新 `learning-config.yaml`
2. 在 `progress.md` 会话日志中记录配置变更
3. 从下一轮开始应用新配置

---

## 配置优先级

1. **special_modes** 最高优先级（临时覆盖其他配置）
2. **学生实时指令**（"这个直接告诉我"）次优先级
3. **配置文件** 默认优先级
4. **导师判断**（学生连续卡壳时，导师可临时降低难度）

---

## 配置与教学原则的关系

配置文件控制**教学策略**，但不违反**教学原则**：

- 即使在 `direct` 模式下，仍然要验证学生理解（只是验证方式更轻量）
- 即使在 `sprint` 模式下，仍然要维护概念之间的逻辑链条
- 即使在 `memorization_aided` 模式下，仍然要在阶段收尾时做费曼复述

**配置文件是"油门"，教学原则是"刹车"。**
