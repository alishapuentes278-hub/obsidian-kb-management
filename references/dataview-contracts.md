# Dataview 数据契约

所有被 Dataview 查询的文件必须遵守以下 YAML frontmatter 规范。

## 项目文件 (`项目总控/*.md`) 必须字段

```yaml
---
type: project         # 必须
status: 进行中        # 必须: 已完成 | 进行中 | 论文写作中 | 未开始
health: 85            # 必须: 0-100
risk: 低             # 必须: 正常 | 低 | 关注 | 高
code_status: 已完成   # 可选: 毕业论文项目用
thesis_status: 已完成 # 可选: 毕业论文项目用
tags: [毕业设计, 项目, ...]
---
```

## 任务文件 (`任务跟踪/*.md`) 必须字段

```yaml
---
type: task            # 必须
status: open          # 必须: open | in_progress | 已完成
priority: 高          # 必须: 高 | 中 | 低
workflow: A-程序设计  # 必须（Dataview 按此分组）
source: 监控发现       # 必须
tags: [毕业设计, 任务]
---
```

## 里程碑文件 (`里程碑/*.md`) 必须字段

```yaml
---
type: milestone       # 必须
workflow: 程序设计     # 必须
phase: A1-A7          # 必须
status: 已完成         # 必须
tags: [毕业设计, 里程碑]
---
```
