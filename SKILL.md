---
name: obsidian-kb-management
description: 【强制预加载】Obsidian 毕业设计知识库管理系统 — 在涉及任何 Obsidian vault 操作、知识库编译/审计、项目数据同步前必须首先加载本 skill。包含 Vault 目录结构、Dataview 数据契约、Agent 自动维护规则（P-1/P-2/K-1/K-2/K-3）、知识库里程碑、项目清单。这是一组执行规则而非参考材料——不加载=无规则裸跑。触发词：Obsidian、知识库、图谱、compile wiki、审计知识库、编译知识库、Dataview、更新AGENTS。
---

# Obsidian 知识库管理系统

> ⚠️ **本 skill 是执行规则，不是参考材料。** 任何 Obsidian vault 操作前必须首先加载本 skill 建立运行上下文，否则 Agent 不知道 Dataview 数据契约和自动维护规则。
>
> 基于 Karpathy "LLM Knowledge Bases" — 知识库是 LLM 的领地，人只负责审核方向和提供源材料。
> 位置: `D:\问答\毕业设计`（Obsidian Vault + Dataview 插件）

## 强制预加载规则

**在执行以下任何操作前，必须首先加载本 skill:**

| 操作类型 | 加载后读取 | 强制执行 |
|---------|-----------|---------|
| 创建/更新 Obsidian 文件 | `references/dataview-contracts.md` | ✅ YAML frontmatter 必须符合契约 |
| 编译知识库 | `references/auto-maintenance.md` 规则 K-1 | ✅ 沿固定管道执行 |
| 审计知识库 | `references/auto-maintenance.md` 规则 K-2 | ✅ 五项检查不可跳过 |
| 操作项目代码后 | `references/auto-maintenance.md` 规则 P-1/P-2 | ✅ 状态必须同步 |
| Q&A 完成后 | `references/auto-maintenance.md` 规则 K-3 | ✅ 结果必须归档 |

## 架构总览

```
Vault (D:\问答\毕业设计)
  ├── _仪表盘.md              ← Dataview 项目总览 + 待办
  ├── 项目总控/               ← 项目文件 (type=project)
  ├── 任务跟踪/               ← 任务文件 (type=task)
  ├── 里程碑/                 ← 里程碑文件 (type=milestone)
  ├── 知识库/                 ← 技术知识点 wiki
  │   ├── 核心/ 重要/ 扩展/   ← 按重要性分层
  │   ├── 原料/               ← Karpathy raw/ 管道入口
  │   ├── 输出/               ← Q&A 输出归档
  │   ├── _知识库迭代机制.md  ← 迭代管道 v2.0
  │   └── _迭代日志.md        ← 变更记录
  └── 监控日志/
```

## 参考文件导航

| 文件 | 内容 | 何时加载 |
|------|------|---------|
| [vault-structure.md](references/vault-structure.md) | Vault 目录结构 + 项目清单 + 技术栈全景 | 需要了解项目全貌时 |
| [dataview-contracts.md](references/dataview-contracts.md) | YAML frontmatter 规范（项目/任务/里程碑） | 创建/更新 Obsidian 文件时（强制）|
| [auto-maintenance.md](references/auto-maintenance.md) | 5 条 Agent 自动维护规则 + 知识库里程碑 | 操作完成后同步数据时（强制）|

## 当前项目速查

| 项目 | 技术栈 | 状态 |
|:---|:---|:---|
| 大学生运动打卡与健康数据分析平台 | Spring Boot 3.2 + MyBatis-Plus + Thymeleaf | 答辩准备中 |
| 城市空气质量影响因素分析 | Python Pandas + Matplotlib | ✅ 已完成 |
| 图书管理系统 | Spring Boot 2.7 + MyBatis + Vue2 + Jsoup | ✅ 已完成 |
| 教学评价管理系统 | Spring MVC 5.2 + MyBatis + JSP + Druid | ✅ 已完成 |
| 故障报修管理系统 | Spring MVC 5.0 + MyBatis-Plus + Vue2 + Druid | ✅ 评估完成 |
