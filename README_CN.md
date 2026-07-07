# 怒笔（FuryPen）

> AI长篇小说一致性写作系统 — 一个真正写完了一本34章小说的 Skill

**怒笔（FuryPen）** 是一个基于 WorkBuddy Skill + Memory 架构的长篇小说一致性写作系统。它不是"帮你写一段话"的工具——它是"让AI能写完整本书而不前后矛盾"的系统。

核心解决三个问题：
- **上下文窗口装不下全书** → Bible 按需注入，每章只加载当前需要的设定
- **AI无持久状态** → run-state.md 状态机 + S4 事实提取回写
- **无一致性闸门** → genre-config 类型定制校验 + S5分层审查 + S8全局终审

## 架构总览

```
Bible（持久化层）   →   Loop（执行层）   →   Gate（控制层）
   meta.md                 S2 上下文注入        genre-config
   characters/             S3 撰写章节           check_priority
   worldbuilding/          S4 事实提取回写       HARD/SOFT分级
   foreshadowing.md        S5 一致性审查
   lorebook.md             S6 场景扩写
   progression.md          S7 修订重写
                           S8 全局终审（10维度）
```

## 8个子Skill一览

| Skill | 功能 | 触发 |
|-------|------|------|
| S1 | 小说初始化：热点菜单→Q&A→生成bible | 一次性 |
| S2 | 上下文注入：按需加载设定→组装提示词 | 每章自动 |
| S3 | 撰写章节：写前自检→草稿→定稿 | 每章 |
| S4 | 事实提取回写：8维度→回写bible | 每章/批量 |
| S5 | 一致性审查：HARD拦截→SOFT放行 | 每章自动 |
| S6 | 场景扩写：定位→注入→扩写→替换 | 按需 |
| S7 | 修订重写：定位→注入→局部重写→验证 | 自动/手动 |
| S8 | 全局终审：10维度跨章节扫描→报告 | 全书完成 |

## 核心特色

- **类型定制一致性闸门（独创）**：规则怪谈/末世生存/都市异能/悬疑推理/通用，每种独立配置check_priority
- **快速连载模式**：跳过逐章审阅，整本写完再改
- **草稿/精修两遍**：draft模式速度优先，polish模式质量优先
- **字数动态适应**：按悬念级别 weight 系数自动调节篇幅
- **批量伏笔扫描**：全书完成后自动从正文识别伏笔埋设/回收
- **S8 10维度全局终审**：孤儿伏笔/信息泄漏/规则漂移/角色掉线/命名一致性

## 实战验证

FuryPen 实际写完了一本 34 章的长篇小说《废品编号007》（又名《愤怒》），约8万字，5卷34章+序幕+尾声。

- 全程快速连载模式，无人工干预
- S8全局终审结果：跨章信息泄漏0处，规则漂移0处，伏笔断裂0处
- 3轮迭代（v1→v3）全部由实战反馈驱动

## 快速开始

1. 确保已安装 [WorkBuddy](https://www.codebuddy.cn)
2. 将本技能目录放置到 `~/.workbuddy/skills/fury-pen/`
3. 在聊天中输入 `写小说` 触发 S1 初始化流程
4. 按 Q&A 引导填入设定 → 系统自动生成完整 bible
5. 输入 `写第1章` → 自动进入 S2→S3→S4→S5 写作循环

## 目录结构

```
~/.workbuddy/skills/fury-pen/
├── SKILL.md                          # 主流程定义（S1-S8完整步骤）
├── references/
│   ├── hot-directions.md             # 4桶×4子方向热点菜单
│   ├── context-assembly-template.md   # S2上下文组装模板
│   ├── extraction-rules.md           # S4 8维度提取规则
│   ├── consistency-check-rules.md    # S5校验方法
│   ├── self-check-rules.md           # S3写前自检清单
│   ├── global-audit-rules.md         # S8 10维度终审规则
│   ├── outline-extension.md          # 大纲自动续展
│   ├── foreshadowing-auto-extract.md # 批量伏笔自动提取
│   └── genre-config/                 # 5个类型配置
│       ├── 规则怪谈.md
│       ├── 末世生存.md
│       ├── 都市异能.md
│       ├── 悬疑推理.md
│       └── 通用.md
├── assets/
│   ├── bible-templates/              # Bible文件模板（20个）
│   │   ├── meta.md / core-rules.md / outline.md
│   │   ├── character.md / character-index.md
│   │   ├── foreshadowing.md / progression.md
│   │   ├── lorebook.md / style-guide.md
│   │   ├── instance.md / instance-index.md
│   │   ├── world-rules.md / location.md
│   │   ├── timeline.md / lore.md
│   │   ├── run-state.md / chapter.md
│   └── tracking-templates/           # Tracking模板（4个）
│       ├── progress.md
│       ├── consistency-log.md
│       ├── rewrite-history.md
│       └── global-audit-log.md
```

## 设计渊源

取五家之长：
- **蛙趣拼文** — 8模块结构 + 伏笔追踪 + 角色成长轨迹
- **NovelCrafter** — Codex百科 + 场景挂载按需注入
- **NovelAI** — Lorebook关键词触发自动注入
- **Sudowrite** — 场景扩写/修订重写
- **AI_NovelGenerator** — 多阶段生成 + 自动一致性检查

**独创**：热点方向选择菜单 + 分阶段Q&A引导初始化 + 类型定制一致性闸门

## 许可

MIT License
