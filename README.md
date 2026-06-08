# obsidian-kb-management

> Obsidian 毕业设计知识库管理系统 —— 基于 Karpathy "LLM Knowledge Bases" 理念，知识库是 LLM 的领地。

## 基本信息

| 字段 | 值 |
|------|-----|
| **名称** | `obsidian-kb-management` |
| **类型** | 强制预加载型 skill（不加载 = 无规则裸跑） |
| **标签** | `Obsidian` `知识库` `Dataview` `YAML` `知识编译` `知识审计` `Karpathy` `毕业设计` |

## 简介

obsidian-kb-management 管理毕业设计的 Obsidian Vault（`D:\问答\毕业设计`）。任何涉及 Obsidian vault 操作——创建/更新文件、知识库编译、审计、项目数据同步——都必须首先加载此 skill 以获取数据契约和自动维护规则。

核心理念来自 Andrej Karpathy 的 "LLM Knowledge Bases"：知识库是 LLM（Agent）的领地，人类只负责审核方向（通过 YAML frontmatter 定义数据契约）和提供源材料（放入 `原料/` 目录等待编译）。

### Vault 结构

```
D:\问答\毕业设计/              ← Obsidian Vault（Dataview 插件）
├── _仪表盘.md                   ← Dataview 项目总览 + 待办任务 + 里程碑
├── 项目总控/                    ← 5个项目文件（YAML: type=project）
├── 任务跟踪/                    ← 28个任务文件（YAML: type=task）
├── 里程碑/                      ← 5个里程碑文件（YAML: type=milestone）
├── 文档中心/                    ← 10个文档状态追踪文件
├── 知识库/                      ← 技术知识点 wiki
│   ├── 核心/  (8篇)            ← importance: 高
│   ├── 重要/  (6篇)            ← importance: 中
│   ├── 扩展/  (2篇)            ← importance: 低
│   ├── 原料/  (5子目录)        ← Karpathy raw/ 管道入口
│   ├── 输出/  (3子目录)        ← Q&A 输出归档
│   ├── _知识库迭代机制.md       ← 迭代管道 v2.0
│   ├── _迭代日志.md             ← 每次迭代的变更记录
│   └── _知识图谱.md             ← 学习路径导航
├── 监控日志/
└── 客户/
```

### 三条自动维护规则（强制执行）

**P-1 项目数据同步**: Agent 操作项目代码后 → 必须同步更新 `项目总控/*.md` 状态字段（status / health / risk）

**P-2 新项目自动登记**: Agent 新建/导入项目 → 在 `项目总控/` 创建 .md + 完整 YAML frontmatter + 更新 `_项目总控库.md`

**K-1 知识库编译**: 听到"编译知识库"/"compile wiki" → 扫描 `原料/` → 提取概念 → 匹配现有文章 → 增量更新或新建

**K-2 知识库审计**: 听到"审计知识库"/"健康检查" → 五项检查（一致性/完整性/新鲜度/连接发现/漏洞扫描）→ 写入 `_迭代日志.md`

**K-3 Q&A 输出归档**: Agent 基于知识库完成复杂问答后 → 自动归档到 `知识库/输出/分析报告/` + 回链引用文章

### Dataview 数据契约

所有被 Dataview 查询的文件必须遵守统一的 YAML frontmatter 规范：

```yaml
# 项目文件
---
type: project         # 必须
status: 进行中        # 已完成 | 进行中 | 论文写作中 | 未开始
health: 85            # 0-100
risk: 低             # 正常 | 低 | 关注 | 高
---
```

### 知识库规模里程碑

| 阶段 | 目标 | 状态 |
|------|------|------|
| 当前 | 21 篇文章 / ~12,000 词 | ✅ 已达成 |
| Phase 1 | 50 篇文章 | ⏳ 积累中 |
| Phase 2 | 100 篇文章 / ~40 万词 | 🔒 远期 |
| Phase 3 | 合成数据 + QA 对生成 | 🔒 远期 |
| Phase 4 | 微调专属模型 | 🔒 远期 |

## 触发关键词

Obsidian、知识库、图谱、compile wiki、审计知识库、编译知识库、Dataview、更新AGENTS

## 安装

将整个 `obsidian-kb-management` 文件夹复制到 `%CODEX_HOME%\skills\` 下：

```
C:\Users\<用户名>\.codex\skills\obsidian-kb-management\
├── README.md
├── SKILL.md
└── references\
    ├── auto-maintenance.md
    ├── dataview-contracts.md
    └── vault-structure.md
```

## 依赖关系

| Skill | 关系 | 说明 |
|-------|------|------|
| `grad-design-squad` | 可选搭配 | 毕业设计场景下通常同时活跃 |

## 文件结构

```
obsidian-kb-management/
├── README.md
├── SKILL.md                       ← 架构总览 + 强制预加载协议
└── references/
    ├── auto-maintenance.md        ← 5条Agent自动维护规则 + 知识库里程碑
    ├── dataview-contracts.md      ← 项目/任务/里程碑 YAML frontmatter 规范
    └── vault-structure.md         ← Vault目录结构 + 项目清单 + 技术栈全景
```

## 使用示例

```
用户: "编译知识库"
Agent: [加载 obsidian-kb-management]
      → 读取 references/auto-maintenance.md 规则 K-1
      → 扫描 知识库/原料/ 中的新内容
      → 提取概念 → 匹配现有文章 → 增量更新
      → 写入 _迭代日志.md

用户: "我刚才改了运动打卡平台的代码"
Agent: [加载 obsidian-kb-management]
      → 读取 references/auto-maintenance.md 规则 P-1
      → 更新 项目总控/大学生运动打卡...md 的 health 和 code_status
```

## 注意事项

- 操作 Obsidian 文件时**必须**遵守 Dataview 数据契约，否则仪表盘查询会断裂
- 知识库编译沿固定管道执行，不可跳过步骤
- 本 skill 与 `project-monitor` 互补——监控发现状态变化，知识库同步数据
