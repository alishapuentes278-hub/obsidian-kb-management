# Vault 目录结构与项目清单

## 完整目录结构

```
D:\问答\毕业设计/
├── _仪表盘.md              ← Dataview 项目总览 + 待办任务 + 里程碑
├── 项目总控/               ← 5 个项目文件（YAML frontmatter: type=project）
│   ├── _项目总控库.md
│   ├── 大学生运动打卡与健康数据分析平台设计与实现.md  ← 毕业设计主项目
│   ├── 城市空气质量影响因素分析.md
│   ├── 图书管理系统.md
│   ├── 故障报修管理系统.md
│   └── 教学评价管理系统.md
├── 任务跟踪/               ← 28 个任务文件（YAML frontmatter: type=task）
├── 里程碑/                 ← 5 个里程碑文件（YAML frontmatter: type=milestone）
├── 文档中心/               ← 10 个文档状态追踪文件
├── 知识库/                 ← 技术知识点 wiki
│   ├── 核心/  (8 篇)       ← importance: 高
│   ├── 重要/  (6 篇)       ← importance: 中
│   ├── 扩展/  (2 篇)       ← importance: 低
│   ├── 原料/  (5 子目录)   ← Karpathy raw/ 管道入口
│   ├── 输出/  (3 子目录)   ← Q&A 输出归档
│   ├── _知识库迭代机制.md  ← 迭代管道 v2.0
│   ├── _迭代日志.md        ← 每次迭代的变更记录
│   └── _知识图谱.md        ← 学习路径导航
├── 监控日志/
└── 客户/
```

## 当前项目清单

| 项目 | 类型 | 技术栈 | 规模 | 状态 |
|:---|:---|:---|:---|:---|
| 大学生运动打卡与健康数据分析平台 | 本科毕业设计（主） | Spring Boot 3.2 + MyBatis-Plus + Thymeleaf | 17 Java / 43 HTML / 4 表 | 答辩准备中 |
| 城市空气质量影响因素分析 | 本科毕业设计 | Python Pandas + Matplotlib | 数据分析脚本 | ✅ 已完成 |
| 图书管理系统 | 程序设计课程设计 | Spring Boot 2.7 + MyBatis + Vue2 + Jsoup | 37 Java / 24 HTML / 8 表 | ✅ 已完成 |
| 教学评价管理系统 | 程序设计课程设计 | Spring MVC 5.2 + MyBatis + JSP + Druid | 33 Java / 38 JSP / 6 表 | ✅ 已完成 |
| 故障报修管理系统 | 外部仓库评估导入 | Spring MVC 5.0 + MyBatis-Plus + Vue2 + Druid | 127 Java / 138 Vue / 13 表 | ✅ 评估完成 |

### 技术栈全景

```
运动打卡 (Boot 3.2) ← 最新
图书管理 (Boot 2.7) ← 过渡
教学评价 (MVC 5.2)  ← 传统
故障报修 (MVC 5.0)  ← 最老
                ↓
  Spring MVC 5.0 → 5.2 → Boot 2.7 → Boot 3.2 完整演进路径
```

### 认证方案演进

```
Session Interceptor (教学评价) → Token Interceptor (故障报修) → Spring Security + JWT (运动打卡)
```
