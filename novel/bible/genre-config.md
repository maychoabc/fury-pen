# 类型配置：星际军事科幻

## 基本信息
genre: 星际军事科幻
description: 底层AI崛起+星际战争+三大帝国争霸的太空歌剧。核心爽感来自军衔权限解锁和战场维度扩展。

## 必填 bible 模块

- meta.md
- genre-config.md（从本文件复制）
- core-rules.md（AI系统规则+三大帝国军事体系）
- outline.md
- characters/
- characters/_index.md
- worldbuilding/
- worldbuilding/rules.md（星际科技体系+三大帝国法则）
- worldbuilding/locations.md（三大帝国核心星球+战场星球）
- worldbuilding/timeline.md（星际战争时间线）
- worldbuilding/lore.md（世界真相：废品判定是镇压）
- foreshadowing.md
- progression.md（军衔+权限解锁+战力维度追踪）
- lorebook.md
- style-guide.md

## 一致性校验优先级

1. 战力权限一致性
   level: HARD（一票否决）
   sources: [progression.md]
   description: 007的当前军衔和权限等级决定了它能指挥的战场维度。低权限指挥高维度战场=硬违规。

2. 世界规则遵守
   level: HARD（一票否决）
   sources: [worldbuilding/rules.md, core-rules.md]
   description: 三大帝国的科技体系、军事规则、AI限制法规不能被后续章节无视。

3. AI设定一致性
   level: HARD（一票否决）
   sources: [characters/007.md, core-rules.md]
   description: 007的能力边界（情感模块故障的代价和优势）必须一致。它不能突然表现出完美AI的能力。

4. 时间线合理性
   level: SOFT
   sources: [worldbuilding/timeline.md]
   description: 星际战争的时间线、舰队移动时间、通讯延迟是否合理。

5. 伏笔状态
   level: SOFT
   sources: [foreshadowing.md]
   description: 废品真相伏笔、三大帝国政治伏笔是否按计划推进和回收。

6. 人物关系演变
   level: SOFT
   sources: [characters/*/关系网]
   description: 仇铁从敌对到战友、001从竞争到崩溃、林曦从陌生到知己的转变是否有足够事件支撑。

## 初始化 Q&A 定制追加

phase1_extra:
  - "废品定义：007被判定废品的具体原因是什么？（情感模块故障？战术偏差率过高？设计用途错位？）"
  - "AI社会地位：在这个文明中AI是工具级、半公民级还是公民级？"
  - "星际格局：几个主要文明/帝国？各自特征？"
  - "成长系统：007如何成长？军衔权限解锁？硬件升级？双线？"
  - "战力体系：从机甲到舰队到联军的维度阶梯怎么分？"
  - "结局走向：胜利+改变秩序？胜利+讽刺反转？牺牲型？"
  - "世界真相（作者视角）：有什么秘密是读者慢揭开的？"

phase2_extra:
  - "完美AI'001'和007的对照关系怎么设计？（001在哪里出场？崩溃的触发点是什么？）"
  - "帝国公主林曦在什么场景下与007相遇？"
  - "007有没有'人类外表'？还是纯数字形态？"

phase3_extra:
  - "第一章开局：007在什么处境下起步？（销毁室？学院？后勤？）"
  - "第一个战场爽点：007用什么非标准操作完成不可能的反击？"

phase4_extra:
  - "废品真相伏笔的埋设节奏：在第几卷开始暗示？第几卷引爆？"
  - "三大帝国之间的政治伏笔：什么事件会改变帝国格局？"
